---
layout: post
title: "Xerox Printer Showing Up As Offline"
headline: Able to ping and browse the web interface.
description: Disable SNMP Status Enabled under Port Configuration.
categories: IT
tags: 
  - how-to
  - itunes
published: true
---

### Problem: 
You are able to ping printer and access printer via web browser. However, printer shows Offline on the printer server.

![Desktop Folder](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline.png)

### Solution: 
Uncheck SNMP Status Enabled under Port Configuration

### Procedure:
1. Right Click Printer > Properties > Ports

![Desktop Folder](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline_1.png)

2. Select the port associated with the printer  > Configure Port

![Desktop Folder](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline_2.png)

3. Under Port Settings > Untick SNMP Status Enabled > OK > Close

![Desktop Folder](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline_3.png)


----------

### References:

1. https://community.spiceworks.com/topic/457808-can-ping-printer-and-access-web-interface-but-cannot-print-via-network
