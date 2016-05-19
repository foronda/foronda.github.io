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
featured: true
---

<section id="table-of-contents" class="toc">
  <header>
    <h3 >Contents</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->

### Overview

After Juniper Core switch configurations and network testing. The next step is to initiate migration of servers and workstations onto the new VLAN subnet. This document covers migrating the current Windows Server 2012 Failover Cluster with a File Server role onto a new subnet or network.  The File server cluster infrastructure utilizes two VM file server nodes with VMware 3-Node clustering with vDS VLAN networking in place. 

![File Server Cluster Design](https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs0.png)

### Procedure

##### Step 1. Add Network Interfaces to VM File Server Nodes

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

##### Step 2. Assign Network Address to the File Server Nodes

- Assign Static IP Address to new Network Interface. Repeat for both nodes.
	- Right Click **Network Interface** > **Properties** > **Internet Protocol Version 4** > **Properties**. Enter IP address
		<figure class="first">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs6.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
	- Disable NetBIOS over TCP/IP
		<figure class="first">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs7.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
	- On the File Server Nodes, flush and register dns by running the following commands on CMD. Upon running the command, each nodes should now have two IP addresses binded to it. 
		 - ``` ipconfig /flushdns ```
		 - ``` ipconfig /registerdns ```
	- Launch DNS manager and verify that the new IP addresses have been registered.
		<figure class="first">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs8.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>

##### Step 3. Add New Network IP to File Server Role

- Allow Cluster Network Communication and Allow clients to connect through this network.
	- Launch Failover Cluster Manager > **Networks**. Right Click on new network > **Properties**
		<figure class="first">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs9.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
	- Check the radio button *Allow cluster network communication in this network*. Check the box *Allow clients to connect through this network*.
		<figure class="first">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs9b.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
- Add New IP Address to the File Server Role
	- Click **Roles** > **Resources** > Right Click **Name** > **Properties**
		<figure class="first">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs10.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
	- Click **Add**. Select the new network and assign the file server role a static IP address. 
		<figure class="second">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs11.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
		<figure class="first">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs12.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>
	- You should now have two network interfaces tied to your File Server Role. Ensure that Publish PTR Records is check. In doing so, new networks binded to this role will be published to the DNS server.  Verify that both IP addresses are online.
		<figure class="second">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs13.png" style="padding-bottom: 5px; border:1px solid gray">
			<img src="https://dl.dropboxusercontent.com/u/33327425/images/it/network-infrastructure-upgrade/file-server-cluster/fs14.png" style="padding-bottom: 5px; border:1px solid gray">
		</figure>

##### Step 4. Switchover File Server Role to New Network
- Under Roles > File Server > Server Name. Right click Old Network > Take Offline.




----------

### References

1. https://community.spiceworks.com/topic/457808-can-ping-printer-and-access-web-interface-but-cannot-print-via-network
