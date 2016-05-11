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

### Solution: 
Uncheck SNMP Status Enabled under Port Configuration

### Procedure:
1. Right Click Printer > Properties > Ports
2. Select the port associated with the printer  > Configure Port
3. Under Port Settings > Untick SNMP Status Enabled > OK > Close


----------

### References:

1. https://community.spiceworks.com/topic/457808-can-ping-printer-and-access-web-interface-but-cannot-print-via-network
