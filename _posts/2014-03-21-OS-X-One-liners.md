---
layout: post
title: "OS X One Liners"
description: "OS X  One Liners."
category: articles
tags: [OS X, Bash, Python, One Liners]
comments: false  
---
OS X one liners I have created or collected. All have been tested on Mavericks.

<br>


```killall Microsoft\ Excel```  

This would kill the Microsoft Excel process, but what if we wanted to kill all Microsoft processes?

```kill $(ps axc | grep -i Microsoft | awk '{print $1} ')```<br><br>

Kill all applications running from /Users folder.

```ps -ef | grep /Users | awk '{print $2}' | xargs kill```<br><br>

Reset Printing System

```lpstat -p | cut -d' ' -f2 | xargs -I{} lpadmin -x {}```<br><br>

Curl outside network information. Thanks to ifconfig.me

```curl ifconfig.me/all```<br><br>

Outside IP address only

```curl ifconfig.me```<br><br>

Display MAC Address of default interface

```netstat -rn | awk '/default/ { print $NF }' | head -1 | xargs -I {}  ifconfig {} | awk '/ether/ {print $2}'```<br><br>

```lsof -i -n -P | grep -e "$(ps aux | grep node | grep -v grep | awk -F' ' '{print $2}' | xargs | awk -F' ' '{str = $1; for(i = 2; i < NF; i++) {str = str "\\|" $i} print str}')"```
<br><br>

[Force delete of Google Chrome Google-related local storage, make Gmail Offline work again](http://www.commandlinefu.com/commands/view/12410/force-delete-of-google-chrome-google-related-local-storage-make-gmail-offline-work-again) 

```/bin/rm -f ~/Library/Application\ Support/Google/Chrome/Default/Local\ Storage/*google*```


[List OSX applications and versions](http://www.commandlinefu.com/commands/view/12107/list-osx-applications-and-versions.)

```find /Applications -type d -maxdepth 1 -exec sh -c 'echo "{}"; (plutil -convert xml1 -o - "{}/Contents/Info.plist" | xpath /dev/stdin "concat(\"v\", /plist/dict/string[preceding-sibling::key[1]=\"CFBundleShortVersionString\"]/node())" 2>/dev/null)' \;```


Serve current directory via Http on port 8000
```python -m SimpleHTTPServer```



Sources

[commandlinefu.com](http://www.commandlinefu.com)