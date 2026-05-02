# Network Infrastructure & Security Monitoring Lab

## Overview

This project documents a virtual IT infrastructure lab built with pfSense, VMware, Windows Server, Windows 11, and Splunk. The goal of the lab was to practice network segmentation, DNS/DHCP configuration, Active Directory domain connectivity, Windows log collection, and basic authentication monitoring.

The lab simulates a small internal network where a Windows Server provides domain services and a Windows 11 client joins the domain. Splunk was used to centralize Windows Security logs and analyze authentication events such as failed logons.

## Lab Environment

- VMware
- pfSense
- Windows Server
- Windows 11 Client
- Active Directory Domain Services
- DNS / DHCP
- Splunk Enterprise
- Splunk Universal Forwarder

## Network Design

The lab used pfSense to separate WAN and LAN traffic and provide internal network routing. The Windows Server was configured with a static IP address and used for domain services, DNS, and authentication. The Windows 11 client was connected to the internal LAN and joined to the domain.

Example internal network:

```text
WAN / Internet
     |
  pfSense
     |
LAN: 10.0.10.0/24
     |
Windows Server: 10.0.10.10
Windows 11 Client: DHCP / Domain Joined
Splunk Server: Log Monitoring
