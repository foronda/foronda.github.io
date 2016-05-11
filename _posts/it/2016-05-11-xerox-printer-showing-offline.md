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

![Xerox Offline](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline.png)

### Solution: 
Uncheck SNMP Status Enabled under Port Configuration

### Procedure:

- Right Click Printer > Properties > Ports

![Xerox Ports](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline_1.png)

- Select the port associated with the printer  > Configure Port

![Configure Ports](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline_2.png)

- Under Port Settings > Untick SNMP Status Enabled > OK > Close

![SNMP](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline_3.png)


----------

### References:

1. https://community.spiceworks.com/topic/457808-can-ping-printer-and-access-web-interface-but-cannot-print-via-network
