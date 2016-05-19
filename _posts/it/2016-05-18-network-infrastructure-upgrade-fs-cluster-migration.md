---
layout: post
title: "Network Infrastructure Upgrade - File Server Cluster Migration"
headline: Migrate Windows Server 2012 File Server Cluster Node
description: Procedure for Migrating File Server Cluster to New Subnet.
categories: IT
tags: 
  - how-to
  - network-infrastructure-upgrade
published: true
---

### Overview: 

After Juniper Core switch configurations and network testing. The next step is to initiate migration of servers and workstations onto the new VLAN subnet. This document covers migrating the current Windows Server 2012 Failover Cluster with a File Server role onto a new subnet or network.  The File server cluster infrastructure utilizes two VM file server nodes with VMware 3-Node clustering with vDS VLAN networking in place. 

### Procedure: 

**Step 1. Add Network Interfaces to VM File Server Nodes**

- Add new network interfaces to the file server nodes Virtual Machine using vSphere Client or vSphere web client. 
	- Right Click VM > **Edit Settings** > **Add** > **Ethernet Adapter** > **Next**
		<figure class="third">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs1.png" style="padding-bottom: 5px; border:1px solid gray">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs2.png" style="padding-bottom: 5px; border:1px solid gray">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs3.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
	- Add the New Network connection, select an adapter type and network connection. In this case I am using VMXNet3 since it is faster, has lower overhead and more stable. E1000 should only be used purely as a fallback for OSes that have no VMware utilities.
		<figure class="second">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs4.png" style="padding-bottom: 5px; border:1px solid gray">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs5.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
	- Repeat this process for other VM nodes.

- Select the port associated with the printer  > **Configure Port**



- Under **Port Settings** > Untick **SNMP Status Enabled** > **OK* > **Close**

![SNMP](https://dl.dropboxusercontent.com/u/33327425/images/it/xerox_offline_3.png)


----------

### References:

1. https://community.spiceworks.com/topic/457808-can-ping-printer-and-access-web-interface-but-cannot-print-via-network
