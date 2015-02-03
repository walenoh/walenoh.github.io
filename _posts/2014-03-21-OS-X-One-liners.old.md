---
layout: post
title: "OS X One Liners"
description: "OS X Bash One Liners."
category: articles
tags: [OS X, Bash, One Liners]
comments: false  
---

A quick OS X one liner to kill Microsoft Database Daemon

```kill $(ps -ef | grep -i Microsoft | grep -v grep | awk '{print $2} ')```