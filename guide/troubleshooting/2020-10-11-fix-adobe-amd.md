---
layout: post
title: Fix Adobe su AMD
date:   2020-10-11 7:00:00 -0600
permalink: /guide/troubleshooting/adobe-amd
---

Uno dei problemi piú comuni di macOS su CPU AMD é il crash delle applicazioni della suite Adobe. Tuttavia, esiste una procedura che permette di fixare questi crash.

## Prerequisiti

- Avere le app della suite Adobe giá installate

## Procedura

> N.B.: questa procedura deve essere eseguita dopo ogni update delle applicazioni.

Aprire il terminale, incollare al suo interno il seguente codice e premere `Invio`.

```
for file in MMXCore FastCore TextModel libiomp5.dylib; do
find /Applications/Adobe* -type f -name $file | while read -r FILE; do
sudo -v
echo "found $FILE"
[[ ! -f ${FILE}.back ]] && sudo cp -f $FILE ${FILE}.back || sudo cp -f ${FILE}.back $FILE
echo $FILE | grep libiomp5 >/dev/null
if [[ $? == 0 ]]; then
dir=$(dirname "$FILE")
[[ ! -f ${HOME}/libiomp5.dylib ]] && cd $HOME && curl -sO https://excellmedia.dl.sourceforge.net/project/badgui2/libs/mac64/libiomp5.dylib
echo -n "replacing " && sudo cp -vf ${HOME}/libiomp5.dylib $dir && echo
rm -f ${HOME}/libiomp5.dylib
continue
fi
echo $FILE | grep TextModel >/dev/null
[[ $? == 0 ]] && echo "emptying $FILE" && sudo echo -n >$FILE && continue
echo "patching $FILE \n"
sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x6A\x00|\x90\x90\x90\x90\x56\xE8\x3A\x00|sg' $FILE
sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x4A\x00|\x90\x90\x90\x90\x56\xE8\x1A\x00|sg' $FILE
done
done
```
Adesso copiare ed incollare il seguente codice nel terminale e dare `Invio`.

```
[ ! -d $HOME/Library/LaunchAgents ] && mkdir $HOME/Library/LaunchAgents
AGENT=$HOME/Library/LaunchAgents/environment.plist
sysctl -n machdep.cpu.brand_string | grep FX >/dev/null 2>&1
x=$(echo $(($? != 0 ? 5 : 4)))
cat >$AGENT <<EOF
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
 <key>Label</key>
 <string>mkl-debug</string>
 <key>ProgramArguments</key>
 <array>
 <string>sh</string>
 <string>-c</string>
    <string>launchctl setenv MKL_DEBUG_CPU_TYPE $x;</string>
 </array>
 <key>RunAtLoad</key>
 <true/>
</dict>
</plist>
EOF
launchctl load ${AGENT} >/dev/null 2>&1
launchctl start ${AGENT} >/dev/null 2>&1

Una volta finito, riavviare il PC.

## Rimuovere il Fix

Per rimuovere il fix, copiare ed incollare il seguente codice nel terminale e premere `Invio`

```
for file in MMXCore FastCore TextModel libiomp5.dylib; do
find /Applications/Adobe* -type f -name $file | while read -r FILE; do
sudo -v
[[ -f ${FILE}.back ]] && echo "found backup $FILE" && sudo mv -f ${FILE}.back $FILE
done
done
AGENT=$HOME/Library/LaunchAgents/environment.plist
if [[ -f $AGENT ]]; then
launchctl unload ${AGENT} >/dev/null 2>&1
launchctl stop ${AGENT} >/dev/null 2>&1
rm -rf $AGENT
fi
```

Una volta finito, riavviare il PC.


# CREDITS

- [@maydayalaska](https://github.com/maydayalaska) e [@dreamwhite](https://github.com/dreamwhite) per la scrittura di questa guida
- [@naveenkrdy](https://github.com/naveenkrdy/) per lo sviluppo del [fix](https://gist.github.com/naveenkrdy/26760ac5135deed6d0bb8902f6ceb6bd)
