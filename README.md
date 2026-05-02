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
```

What I Configured
Deployed a segmented virtual network using pfSense
Configured DNS and DHCP services for internal client connectivity
Joined a Windows 11 client to the Active Directory domain
Enabled Windows audit logging for authentication events
Installed and configured Splunk Universal Forwarder
Ingested Windows Security logs into Splunk
Created Splunk searches to identify failed login activity
Splunk Log Monitoring

Splunk was configured to collect Windows Security logs from the lab environment. This allowed authentication events to be searched, filtered, and visualized.

One of the main event codes analyzed was:

4625 = failed logon attempt

Failed Logon Search

```text
index=main EventCode=4625
| table _time Account_Name Workstation_Name Source_Network_Address IpAddress Logon_Type Failure_Reason
```

This query displays failed logon attempts with key fields such as the account name, workstation name, source network address, logon type, and failure reason.













