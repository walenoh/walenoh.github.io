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


Kill Microsoft Database Daemon

```kill $(ps -ef | grep -i Microsoft\ Database\ Daemon | grep -v grep | awk '{print $2} ')```<br><br>

Kill SyncServices

```kill $(ps -ef | grep -i SyncServices | grep -v grep | awk '{print $2} ')```<br><br>

Kill all applications running from /Users folder

```ps -ef | grep /Users | grep -v grep | awk '{print $2}' | xargs kill```<br><br>

Reset Printing System

```lpstat -p | cut -d' ' -f2 | xargs -I{} lpadmin -x {}```<br><br>

Curl outside network information. Thanks to ifconfig.me

```curl ifconfig.me/all```<br><br>

Outside IP address only

```curl ifconfig.me```<br><br>

Display MAC Address of default interface

```netstat -rn | awk '/default/ { print $NF }' | head -1 | xargs -I {}  ifconfig {} | awk '/ether/ {print $2}'```<br><br>

Serve current directory via Http on port 8000
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```python -m SimpleHTTPServer```