---
layout: post
title: "Network Infrastructure Upgrade - Overview"
headline: "Redesign of flat network to 2-Tier Hierarchical Design"
description: 
categories: 
  - IT
tags: "it,network-design,juniper,vlans,switching,routing"
published: true
modified: ""
imagefeature: ""
mathjax: false
featured: true
comments: false
---

### Overview

Network security is crucial to all network infrastructures, especially in businesses who store sensitive information such as personally identifiable information, credit card numbers, medical health records, etc. As stated by the PCI council, any company that *process*, *store* or *transmit* credit card information, there are compliance requirements that must be met to avoid out of compliance penalties and fines. However, instead of focusing on the checklist compliance requirements, this project aims towards reducing the overall scope and securing the infrastructure beyond PCI compliance. This project is a complete overhaul of the current network infrastructure utilizing unmanaged switches and transitioning to managed switches to achieve the infrastructure needs. Managed switches provide all features of an unmanaged switch but provide the ability to configure, manage, and monitor the local area network. The upgrade to managed switches will provide a greater control over how data travels over the network and who has access to it; increasing overall network security to achieve PCI compliance across the network.

### Network Infrastructure Upgrade Design Goals and Requirements

- PCI Compliance
    - Scope reduction through logical network segmentation.
    - Isolate senstive traffic and control behavior of traffic.
- Platform longevity and future proof instrastructure. Ease of scalability and expandability.
    -  Support of EMV Devices and Point-to-Point Encryption devices
    -  Support of IP Cameras, Mobile technologies, VoIP, WiFi devices, network storages, etc.
- Increase Network Security
    - Access Control Lists, Switch Port Management, MAC Address filtering 
    - Prevent unathorized access.
- Minimize Network Downtime
    -  Redundant and resilient design removes single point of failure at the core. Ability to install security patches and make configuration changes at core without loss of connectivity.
- Reduced operational expenses.
    -  Ability to remotely monitor network health and traffic (through SNMP) and troubleshoot within the local area network.
    - Port mirroring to diagnose problems without taking the network out of service.
- Achieve industry network standardization.

### Proposed Solution

#### Juniper Two-tier hierarchical network model

- Features
    - Redundant and resilient design with Two-tier hierarchical network model utlizing Virtual Chassis and Link Aggregation.
    - Maintenance without losing connection to datacenter. 
    - Easy rollback feature in case of misconfiguration. 
    - Separate control and data plane to restart processes without full reboot. 
    - Established switch manufacturer with Junos operating system and virtual chassis along with centralized management. Comparable to Cisco and HP with network standards and technologies.

<center> <b><u>Two-tier Network Model (Collapsed Core and Distribution Layer)</u></b> </center>

![2-Tier Network Model](https://dl.dropboxusercontent.com/u/33327425/images/it/2-Tier_Network_Design.png)

### Implementation Phases

#### I. Network Redesign

- Design new network infrastructure to meet goals and requirements.
- Understand traffic types within the infrastructure, implement segmentation and ACL's for sensitive traffic types.
- Run new and additional Cat6 cabling to eliminate daisy chained switches and single point of failures. 
- Create VLANs for the different traffic types. Allocate IP ranges for these VLANs.
 
#### II. Network Standardization and Documentation

- Establish network cable naming and labelin standards to easily identify switch port connections, uplinks, and network traffic type.

#### III. Understand and Research Junos OS 

- Research security best practices and implementation of Juniper networking hardware. 

#### III. Core Switch Configurations

- Implementation of Juniper virtual vhassis, link aggregation, VLANs, inter-vlan routing, DHCP-relay, stateless firewall filters, switch and port security.
- VLAN trunking to Firewall for DMZ and Guest related traffic.

#### IV. Access Switch Configurations

- Create standard security template for access switches. 
- 
