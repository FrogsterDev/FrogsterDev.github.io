---
layout: learning
title: "Junior Cybersecurity Analyst HTB"
status: "In Progress"
progress: 35.6
duration: "17 days"
description: "Study notes and writeups for the Junior Cybersecurity Analyst path from HTB"
resources:
    - title: "HackTheBox Academy"
      description: "Interactive learning platform for ethical hacking"
      url: "https://academy.hackthebox.com/"
progress_notes: |
  ##### *Day 1:*

  **Introduction to information security** ✔ [*Complete*](https://academy.hackthebox.com/achievement/786250/293)
  
  ##### *Day 2:*
  
  **Network Foundations** ✔ [*Complete*](https://academy.hackthebox.com/achievement/786250/289) 

  ##### *Day 3:*
  **Introduction to Networking** ✔ [*Complete*](https://academy.hackthebox.com/achievement/786250/34)

  ##### *Day 4:*
  **Linux Fundamentals** ✔ [*Complete*](https://academy.hackthebox.com/achievement/786250/18)
  
  ##### *Day 5:*
  **Introduction to Bash Scripting** ✔ [*Complete*](https://academy.hackthebox.com/achievement/786250/21)
---

# Notes

### Networking

- [Networking Key terminology](#networking-key-terminology)
- [Common TCP protocols](#common-tcp-protocols---ports)
- [Common UDP protocols](#common-udp-protocols---ports)
- [Authentication protocols](#authentication-protocols)

### Linux

- [File System Hierarchy](#linux-file-system-hierarchy)
- [Commands Cheetsheet](#commands-cheatsheet)
- [RegEx](#regular-expresions)
- [File permissions management](#file-permissions-menagement)
- [Exercises](#exercises)
- [Task Scheduling](#task-scheduling)
    - [Systemd](#systemd)
    - [Cron](#cron)
- [Mounting](#mounting)
- [Dockerization - Docker](#dockerization---docker)
    - [How to install docker-engine](#how-to-install-docker-engine)
    - [Dockerfile](#dockerfile)
    - [Docker build](#docker-build)
    - [Docker run](#docker-run)
    - [Docker management](#docker-management)
- [LXC - Linux containers](#lxc---linux-containers)
    - [Installation](#installation-lxc)
    - [Creating LCX Container](#creating-lxc-container)
    - [Containers Management](#lxc-containers-management)
    - [Securing LXC](#securing-lxc)
    - [Exercises for later](#exercises-for-later-for-lxc)
- [Linux Networking](#linux-networking)
    - [Activate network interface](#activate-network-interface)
    - [Assign IP address to an interface](#assign-ip-address-to-an-interface)
    - [Assign a netmask to an interface](#assign-a-netmask-to-an-interface)
    - [Assign the route to an interface](#assign-the-route-to-an-interface)
    - [DNS Settings](#dns-settings)
    - [System hardening](#system-hardening)
- [Remote desktop](#remote-desktop)
    - [X11Forwarding](#x11forwarding)
    - [TigerVNC](#tigervnc)
        - [Installation](#installation-tigervnc)
        - [Configuration](#configuration-tigervnc)
        - [Start VNC Server](#start-vncserver)
        - [List sessions](#list-sessions-vncserver)
        - [Setting up an ssh tunel](#setting-up-an-ssh-tunel-vncserver)
        - [Connect to the server](#connect-to-the-server-vncserver)
- [Linux Hardening](#linux-hardening)
    - [Block Traffic](#block-traffic)
    - [Firewall Setup](#firewall-setup)
- [Shortcuts](#shortcuts)

### Bash scripting

- [File Operators](#file-operators-bash)

### Windows

- [CheatSheet](#windows-cheatsheet)
- [Creating a Network Share](#creating-a-network-share-windows)
- [Connecting to Network Share](#connecting-to-network-share-windows)
- [Windows Execution Policy](#windows-execution-policy)

## Networking Key terminology


| **Protocol**                                      | **Acronym** | **Description**                                                                                                                                                                                                                                                                                |
| ------------------------------------------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wired Equivalent Privacy                          | `WEP`       | WEP is a type of security protocol that was commonly used to secure wireless networks.                                                                                                                                                                                                         |
| Secure Shell                                      | `SSH`       | A secure network protocol used to log into and execute commands on a remote system                                                                                                                                                                                                             |
| File Transfer Protocol                            | `FTP`       | A network protocol used to transfer files from one system to another                                                                                                                                                                                                                           |
| Simple Mail Transfer Protocol                     | `SMTP`      | A protocol used to send and receive emails                                                                                                                                                                                                                                                     |
| Hypertext Transfer Protocol                       | `HTTP`      | A client-server protocol used to send and receive data over the internet                                                                                                                                                                                                                       |
| Server Message Block                              | `SMB`       | A protocol used to share files, printers, and other resources in a network                                                                                                                                                                                                                     |
| Network File System                               | `NFS`       | A protocol used to access files over a network                                                                                                                                                                                                                                                 |
| Simple Network Management Protocol                | `SNMP`      | A protocol used to manage network devices                                                                                                                                                                                                                                                      |
| Wi-Fi Protected Access                            | `WPA`       | WPA is a wireless security protocol that uses a password to protect wireless networks from unauthorized access.                                                                                                                                                                                |
| Temporal Key Integrity Protocol                   | `TKIP`      | TKIP is also a security protocol used in wireless networks but less secure.                                                                                                                                                                                                                    |
| Network Time Protocol                             | `NTP`       | It is used to synchronize the timing of computers on a network.                                                                                                                                                                                                                                |
| Virtual Local Area Network                        | `VLAN`      | It is a way to segment a network into multiple logical networks.                                                                                                                                                                                                                               |
| VLAN Trunking Protocol                            | `VTP`       | VTP is a Layer 2 protocol that is used to establish and maintain a virtual LAN (VLAN) spanning multiple switches.                                                                                                                                                                              |
| Routing Information Protocol                      | `RIP`       | RIP is a distance-vector routing protocol used in local area networks (LANs) and wide area networks (WANs).                                                                                                                                                                                    |
| Open Shortest Path First                          | `OSPF`      | It is an interior gateway protocol (IGP) for routing traffic within a single Autonomous System (AS) in an Internet Protocol (IP) network.                                                                                                                                                      |
| Interior Gateway Routing Protocol                 | `IGRP`      | IGRP is a Cisco proprietary interior gateway protocol designed for routing within autonomous systems.                                                                                                                                                                                          |
| Enhanced Interior Gateway Routing Protocol        | `EIGRP`     | It is an advanced distance-vector routing protocol that is used to route IP traffic within a network.                                                                                                                                                                                          |
| Pretty Good Privacy                               | `PGP`       | PGP is an encryption program that is used to secure emails, files, and other types of data.                                                                                                                                                                                                    |
| Network News Transfer Protocol                    | `NNTP`      | NNTP is a protocol used for distributing and retrieving messages in newsgroups across the internet.                                                                                                                                                                                            |
| Cisco Discovery Protocol                          | `CDP`       | It is a proprietary protocol developed by Cisco Systems that allows network administrators to discover and manage Cisco devices connected to the network.                                                                                                                                      |
| Hot Standby Router Protocol                       | `HSRP`      | HSRP is a protocol used in Cisco routers to provide redundancy in the event of a router or other network device failure.                                                                                                                                                                       |
| Virtual Router Redundancy Protocol                | `VRRP`      | It is a protocol used to provide automatic assignment of available Internet Protocol (IP) routers to participating hosts.                                                                                                                                                                      |
| Spanning Tree Protocol                            | `STP`       | STP is a network protocol used to ensure a loop-free topology in Layer 2 Ethernet networks.                                                                                                                                                                                                    |
| Terminal Access Controller Access-Control System  | `TACACS`    | TACACS is a protocol that provides centralized authentication, authorization, and accounting for network access.                                                                                                                                                                               |
| Session Initiation Protocol                       | `SIP`       | It is a signaling protocol used for establishing and terminating real-time voice, video and multimedia sessions over an IP network.                                                                                                                                                            |
| Voice Over IP                                     | `VOIP`      | VOIP is a technology that allows for telephone calls to be made over the internet.                                                                                                                                                                                                             |
| Extensible Authentication Protocol                | `EAP`       | EAP is a framework for authentication that supports multiple authentication methods, such as passwords, digital certificates, one-time passwords, and public-key authentication.                                                                                                               |
| Lightweight Extensible Authentication Protocol    | `LEAP`      | LEAP is a proprietary wireless authentication protocol developed by Cisco Systems. It is based on the Extensible Authentication Protocol (EAP) used in the Point-to-Point Protocol (PPP).                                                                                                      |
| Protected Extensible Authentication Protocol      | `PEAP`      | PEAP is a security protocol that provides an encrypted tunnel for wireless networks and other types of networks.                                                                                                                                                                               |
| Systems Management Server                         | `SMS`       | SMS is a systems management solution that helps organizations manage their networks, systems, and mobile devices.                                                                                                                                                                              |
| Microsoft Baseline Security Analyzer              | `MBSA`      | It is a free security tool from Microsoft that is used to detect potential security vulnerabilities in Windows computers, networks, and systems.                                                                                                                                               |
| Supervisory Control and Data Acquisition          | `SCADA`     | It is a type of industrial control system that is used to monitor and control industrial processes, such as those in manufacturing, power generation, and water and waste treatment.                                                                                                           |
| Virtual Private Network                           | `VPN`       | VPN is a technology that allows users to create a secure, encrypted connection to another network over the internet.                                                                                                                                                                           |
| Internet Protocol Security                        | `IPsec`     | IPsec is a protocol used to provide secure, encrypted communication over a network. It is commonly used in VPNs, or Virtual Private Networks, to create a secure tunnel between two devices.                                                                                                   |
| Point-to-Point Tunneling Protocol                 | `PPTP`      | It is a protocol used to create a secure, encrypted tunnel for remote access.                                                                                                                                                                                                                  |
| Network Address Translation                       | `NAT`       | NAT is a technology that allows multiple devices on a private network to connect to the internet using a single public IP address. NAT works by translating the private IP addresses of devices on the network into a single public IP address, which is then used to connect to the internet. |
| Carriage Return Line Feed                         | `CRLF`      | Combines two control characters to indicate the end of a line and a start of a new one for certain text file formats.                                                                                                                                                                          |
| Asynchronous JavaScript and XML                   | `AJAX`      | Web development technique that allows creating dynamic web pages using JavaScript and XML/JSON.                                                                                                                                                                                                |
| Internet Server Application Programming Interface | `ISAPI`     | Allows to create performance-oriented web extensions for web servers using a set of APIs.                                                                                                                                                                                                      |
| Uniform Resource Identifier                       | `URI`       | It is a syntax used to identify a resource on the Internet.                                                                                                                                                                                                                                    |
| Uniform Resource Locator                          | `URL`       | Subset of URI that identifies a web page or another resource on the Internet, including the protocol and the domain name.                                                                                                                                                                      |
| Internet Key Exchange                             | `IKE`       | IKE is a protocol used to set up a secure connection between two computers. It is used in virtual private networks (VPNs) to provide authentication and encryption for data transmission, protecting the data from outside eavesdropping and tampering.                                        |
| Generic Routing Encapsulation                     | `GRE`       | This protocol is used to encapsulate the data being transmitted within the VPN tunnel.                                                                                                                                                                                                         |
| Remote Shell                                      | `RSH`       | It is a program under Unix that allows executing commands and programs on a remote computer.                                                                                                                                                                                                   |


## Common TCP protocols - ports


| **Protocol**                                              | **Acronym**  | **Port**                                                                                                                                                                                                                                                                                       | **Description**                                                                                                                                                                    |
| --------------------------------------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Telnet                                                    | `Telnet`     | `23`                                                                                                                                                                                                                                                                                           | Remote login service                                                                                                                                                               |
| Secure Shell                                              | `SSH`        | `22`                                                                                                                                                                                                                                                                                           | Secure remote login service                                                                                                                                                        |
| Simple Network Management Protocol                        | `SNMP`       | `161-162`                                                                                                                                                                                                                                                                                      | Manage network devices                                                                                                                                                             |
| Hyper Text Transfer Protocol                              | `HTTP`       | `80`                                                                                                                                                                                                                                                                                           | Used to transfer webpages                                                                                                                                                          |
| Hyper Text Transfer Protocol Secure                       | `HTTPS`      | `443`                                                                                                                                                                                                                                                                                          | Used to transfer secure webpages                                                                                                                                                   |
| Domain Name System                                        | `DNS`        | `53`                                                                                                                                                                                                                                                                                           | Lookup domain names                                                                                                                                                                |
| File Transfer Protocol                                    | `FTP`        | `20-21`                                                                                                                                                                                                                                                                                        | Used to transfer files                                                                                                                                                             |
| Trivial File Transfer Protocol                            | `TFTP`       | `69`                                                                                                                                                                                                                                                                                           | Used to transfer files                                                                                                                                                             |
| Network Time Protocol                                     | `NTP`        | `123`                                                                                                                                                                                                                                                                                          | Synchronize computer clocks                                                                                                                                                        |
| Simple Mail Transfer Protocol                             | `SMTP`       | `25`                                                                                                                                                                                                                                                                                           | Used for email transfer                                                                                                                                                            |
| Post Office Protocol                                      | `POP3`       | `110`                                                                                                                                                                                                                                                                                          | Used to retrieve emails                                                                                                                                                            |
| Internet Message Access Protocol                          | `IMAP`       | `143`                                                                                                                                                                                                                                                                                          | Used to access emails                                                                                                                                                              |
| Server Message Block                                      | `SMB`        | `445`                                                                                                                                                                                                                                                                                          | Used to transfer files                                                                                                                                                             |
| Network File System                                       | `NFS`        | `111`, `2049`                                                                                                                                                                                                                                                                                  | Used to mount remote systems                                                                                                                                                       |
| Bootstrap Protocol                                        | `BOOTP`      | `67`, `68`                                                                                                                                                                                                                                                                                     | Used to bootstrap computers                                                                                                                                                        |
| Kerberos                                                  | `Kerberos`   | `88`                                                                                                                                                                                                                                                                                           | Used for authentication and authorization                                                                                                                                          |
| Lightweight Directory Access Protocol                     | `LDAP`       | `389`                                                                                                                                                                                                                                                                                          | Used for directory services                                                                                                                                                        |
| Remote Authentication Dial-In User Service                | `RADIUS`     | `1812`, `1813`                                                                                                                                                                                                                                                                                 | Used for authentication and authorization                                                                                                                                          |
| Dynamic Host Configuration Protocol                       | `DHCP`       | `67`, `68`                                                                                                                                                                                                                                                                                     | Used to configure IP addresses                                                                                                                                                     |
| Remote Desktop Protocol                                   | `RDP`        | `3389`                                                                                                                                                                                                                                                                                         | Used for remote desktop access                                                                                                                                                     |
| Network News Transfer Protocol                            | `NNTP`       | `119`                                                                                                                                                                                                                                                                                          | Used to access newsgroups                                                                                                                                                          |
| Remote Procedure Call                                     | `RPC`        | `135`, `137-139`                                                                                                                                                                                                                                                                               | Used to call remote procedures                                                                                                                                                     |
| Identification Protocol                                   | `Ident`      | `113`                                                                                                                                                                                                                                                                                          | Used to identify user processes                                                                                                                                                    |
| Internet Control Message Protocol                         | `ICMP`       | `0-255`                                                                                                                                                                                                                                                                                        | Used to troubleshoot network issues                                                                                                                                                |
| Internet Group Management Protocol                        | `IGMP`       | `0-255`                                                                                                                                                                                                                                                                                        | Used for multicasting                                                                                                                                                              |
| Oracle DB (Default/Alternative) Listener                  | `oracle-tns` | `1521`/`1526`                                                                                                                                                                                                                                                                                  | The Oracle database default/alternative listener is a service that runs on the database host and receives requests from Oracle clients.                                            |
| Ingres Lock                                               | `ingreslock` | `1524`                                                                                                                                                                                                                                                                                         | Ingres database is commonly used for large commercial applications and as a backdoor that can execute commands remotely via RPC.                                                   |
| Squid Web Proxy                                           | `http-proxy` | `3128`                                                                                                                                                                                                                                                                                         | Squid web proxy is a caching and forwarding HTTP web proxy used to speed up a web server by caching repeated requests.                                                             |
| Secure Copy Protocol                                      | `SCP`        | `22`                                                                                                                                                                                                                                                                                           | Securely copy files between systems                                                                                                                                                |
| Session Initiation Protocol                               | `SIP`        | `5060`                                                                                                                                                                                                                                                                                         | Used for VoIP sessions                                                                                                                                                             |
| Simple Object Access Protocol                             | `SOAP`       | `80`, `443`                                                                                                                                                                                                                                                                                    | Used for web services                                                                                                                                                              |
| Secure Socket Layer                                       | `SSL`        | `443`                                                                                                                                                                                                                                                                                          | Securely transfer files                                                                                                                                                            |
| TCP Wrappers                                              | `TCPW`       | `113`                                                                                                                                                                                                                                                                                          | Used for access control                                                                                                                                                            |
| Internet Security Association and Key Management Protocol | `ISAKMP`     | `500`                                                                                                                                                                                                                                                                                          | Used for VPN connections                                                                                                                                                           |
| Microsoft SQL Server                                      | `ms-sql-s`   | `1433`                                                                                                                                                                                                                                                                                         | Used for client connections to the Microsoft SQL Server.                                                                                                                           |
| Kerberized Internet Negotiation of Keys                   | `KINK`       | `892`                                                                                                                                                                                                                                                                                          | Used for authentication and authorization                                                                                                                                          |
| Open Shortest Path First                                  | `OSPF`       | `89`                                                                                                                                                                                                                                                                                           | Used for routing                                                                                                                                                                   |
| Point-to-Point Tunneling Protocol                         | `PPTP`       | `1723`                                                                                                                                                                                                                                                                                         | Is used to create VPNs                                                                                                                                                             |
| Remote Execution                                          | `REXEC`      | `512`                                                                                                                                                                                                                                                                                          | This protocol is used to execute commands on remote computers and send the output of commands back to the local computer.                                                          |
| Remote Login                                              | `RLOGIN`     | `513`                                                                                                                                                                                                                                                                                          | This protocol starts an interactive shell session on a remote computer.                                                                                                            |
| X Window System                                           | `X11`        | `6000`                                                                                                                                                                                                                                                                                         | It is a computer software system and network protocol that provides a graphical user interface (GUI) for networked computers.                                                      |
| Relational Database Management System                     | `DB2`        | `50000`                                                                                                                                                                                                                                                                                        | RDBMS is designed to store, retrieve and manage data in a structured format for enterprise applications such as financial systems, customer relationship management (CRM) systems. |


## Common UDP protocols - ports


| **Protocol**                        | **Acronym**  | **Port**    | **Description**                                                                                                                                    |
| ----------------------------------- | ------------ | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Domain Name System                  | `DNS`        | `53`        | It is a protocol to resolve domain names to IP addresses.                                                                                          |
| Trivial File Transfer Protocol      | `TFTP`       | `69`        | It is used to transfer files between systems.                                                                                                      |
| Network Time Protocol               | `NTP`        | `123`       | It synchronizes computer clocks in a network.                                                                                                      |
| Simple Network Management Protocol  | `SNMP`       | `161`       | It monitors and manages network devices remotely.                                                                                                  |
| Routing Information Protocol        | `RIP`        | `520`       | It is used to exchange routing information between routers.                                                                                        |
| Internet Key Exchange               | `IKE`        | `500`       | Internet Key Exchange                                                                                                                              |
| Bootstrap Protocol                  | `BOOTP`      | `68`        | It is used to bootstrap hosts in a network.                                                                                                        |
| Dynamic Host Configuration Protocol | `DHCP`       | `67`        | It is used to assign IP addresses to devices in a network dynamically.                                                                             |
| Telnet                              | `TELNET`     | `23`        | It is a text-based remote access communication protocol.                                                                                           |
| MySQL                               | `MySQL`      | `3306`      | It is an open-source database management system.                                                                                                   |
| Terminal Server                     | `TS`         | `3389`      | It is a remote access protocol used for Microsoft Windows Terminal Services by default.                                                            |
| NetBIOS Name                        | `netbios-ns` | `137`       | It is used in Windows operating systems to resolve NetBIOS names to IP addresses on a LAN.                                                         |
| Microsoft SQL Server                | `ms-sql-m`   | `1434`      | Used for the Microsoft SQL Server Browser service.                                                                                                 |
| Universal Plug and Play             | `UPnP`       | `1900`      | It is a protocol for devices to discover each other on the network and communicate.                                                                |
| PostgreSQL                          | `PGSQL`      | `5432`      | It is an object-relational database management system.                                                                                             |
| Virtual Network Computing           | `VNC`        | `5900`      | It is a graphical desktop sharing system.                                                                                                          |
| X Window System                     | `X11`        | `6000-6063` | It is a computer software system and network protocol that provides GUI on Unix-like systems.                                                      |
| Syslog                              | `SYSLOG`     | `514`       | It is a standard protocol to collect and store log messages on a computer system.                                                                  |
| Internet Relay Chat                 | `IRC`        | `194`       | It is a real-time Internet text messaging (chat) or synchronous communication protocol.                                                            |
| OpenPGP                             | `OpenPGP`    | `11371`     | It is a protocol for encrypting and signing data and communications.                                                                               |
| Internet Protocol Security          | `IPsec`      | `500`       | IPsec is also a protocol that provides secure, encrypted communication. It is commonly used in VPNs to create a secure tunnel between two devices. |
| Internet Key Exchange               | `IKE`        | `11371`     | It is a protocol for encrypting and signing data and communications.                                                                               |
| X Display Manager Control Protocol  | `XDMCP`      | `177`       | XDMCP is a network protocol that allows a user to remotely log in to a computer running the X11.                                                   |


## Authentication protocols

|**Protocol**|**Description**|
|---|---|
|`Kerberos`|Key Distribution Center (KDC) based authentication protocol that uses tickets in domain environments.|
|`SRP`|This is a password-based authentication protocol that uses cryptography to protect against eavesdropping and man-in-the-middle attacks.|
|`SSL`|A cryptographic protocol used for secure communication over a computer network.|
|`TLS`|TLS is a cryptographic protocol that provides communication security over the internet. It is the successor to SSL.|
|`OAuth`|An open standard for authorization that allows users to grant third-party access to their web resources without sharing their passwords.|
|`OpenID`|OpenID is a decentralized authentication protocol that allows users to use a single identity to sign in to multiple websites.|
|`SAML`|Security Assertion Markup Language is an XML-based standard for securely exchanging authentication and authorization data between parties.|
|`2FA`|An authentication method that uses a combination of two different factors to verify a user's identity.|
|`FIDO`|The Fast IDentity Online Alliance is a consortium of companies working to develop open standards for strong authentication.|
|`PKI`|PKI is a system for securely exchanging information based on the use of public and private keys for encryption and digital signatures.|
|`SSO`|An authentication method that allows a user to use a single set of credentials to access multiple applications.|
|`MFA`|MFA is an authentication method that uses multiple factors, such as something the user knows (a password), something the user has (a phone), or something the user is (biometric data), to verify their identity.|
|`PAP`|A simple authentication protocol that sends a user's password in clear text over the network.|
|`CHAP`|An authentication protocol that uses a three-way handshake to verify a user's identity.|
|`EAP`|A framework for supporting multiple authentication methods, allowing for the use of various technologies to verify a user's identity.|
|`SSH`|This is a network protocol for secure communication between a client and a server. We can use it for remote command-line access and remote command execution, as well as for secure file transfer. SSH uses encryption to protect against eavesdropping and other attacks and can also be used for authentication.|
|`HTTPS`|This is a secure version of the HTTP protocol used for communication on the internet. HTTPS uses SSL/TLS to encrypt communication and provide authentication, ensuring that third parties cannot intercept and read the transmitted data. It is widely used for secure communication over the internet, particularly for web browsing.|
|`LEAP`|LEAP is a wireless authentication protocol developed by Cisco. It uses EAP to provide mutual authentication between a wireless client and a server and uses the RC4 encryption algorithm to encrypt communication between the two. Unfortunately, LEAP is vulnerable to dictionary attacks and other security vulnerabilities and has been largely replaced by more secure protocols such as EAP-TLS and PEAP.|
|`PEAP`|PEAP on the other hand is a secure tunneling protocol used for wireless and wired networks. It is based on EAP and uses TLS to encrypt communication between a client and a server. PEAP uses a server-side certificate to authenticate the server and can also be used to authenticate the client using various methods, such as passwords, certificates, or biometric data. PEAP is widely used in enterprise networks for secure authentication.|

## Linux File System Hierarchy

|**Path**|**Description**|

|---|---|
|`/`|The top-level directory is the root filesystem and contains all of the files required to boot the operating system before other filesystems are mounted, as well as the files required to boot the other filesystems. After boot, all of the other filesystems are mounted at standard mount points as subdirectories of the root.|
|`/bin`|Contains essential command binaries.|
|`/boot`|Consists of the static bootloader, kernel executable, and files required to boot the Linux OS.|
|`/dev`|Contains device files to facilitate access to every hardware device attached to the system.|
|`/etc`|Local system configuration files. Configuration files for installed applications may be saved here as well.|
|`/home`|Each user on the system has a subdirectory here for storage.|
|`/lib`|Shared library files that are required for system boot.|
|`/media`|External removable media devices such as USB drives are mounted here.|
|`/mnt`|Temporary mount point for regular filesystems.|
|`/opt`|Optional files such as third-party tools can be saved here.|
|`/root`|The home directory for the root user.|
|`/sbin`|This directory contains executables used for system administration (binary system files).|
|`/tmp`|The operating system and many programs use this directory to store temporary files. This directory is generally cleared upon system boot and may be deleted at other times without any warning.|
|`/usr`|Contains executables, libraries, man files, etc.|
|`/var`|This directory contains variable data files such as log files, email in-boxes, web application related files, cron files, and more.|

## Bash settings

|**Special Character**|**Description**|
|---|---|
|`\d`|Date (Mon Feb 6)|
|`\D{\%Y-\%m-\%d}`|Date (YYYY-MM-DD)|
|`\H`|Full hostname|
|`\j`|Number of jobs managed by the shell|
|`\n`|Newline|
|`\r`|Carriage return|
|`\s`|Name of the shell|
|`\t`|Current time 24-hour (HH:MM:SS)|
|`\T`|Current time 12-hour (HH:MM:SS)|
|`\@`|Current time|
|`\u`|Current username|
|`\w`|Full path of the current working directory|

## System information - commands


|**Command**|**Description**|
|---|---|
|`whoami`|Displays current username.|
|`id`|Returns users identity|
|`hostname`|Sets or prints the name of current host system.|
|`uname`|Prints basic information about the operating system name and system hardware.|
|`pwd`|Returns working directory name.|
|`ifconfig`|The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters.|
|`ip`|Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.|
|`netstat`|Shows network status.|
|`ss`|Another utility to investigate sockets.|
|`ps`|Shows process status.|
|`who`|Displays who is logged in.|
|`env`|Prints environment or sets and executes command.|
|`lsblk`|Lists block devices.|
|`lsusb`|Lists USB devices|
|`lsof`|Lists opened files.|
|`lspci`|Lists PCI devices.|

## Commands cheatsheet

|**Command**|**Description**|
|---|---|
|`man <tool>`|Opens man pages for the specified tool.|
|`<tool> -h`|Prints the help page of the tool.|
|`apropos <keyword>`|Searches through man pages' descriptions for instances of a given keyword.|
|`cat`|Concatenate and print files.|
|`whoami`|Displays current username.|
|`id`|Returns users identity.|
|`hostname`|Sets or prints the name of the current host system.|
|`uname`|Prints operating system name.|
|`pwd`|Returns working directory name.|
|`ifconfig`|The `ifconfig` utility is used to assign or view an address to a network interface and/or configure network interface parameters.|
|`ip`|Ip is a utility to show or manipulate routing, network devices, interfaces, and tunnels.|
|`netstat`|Shows network status.|
|`ss`|Another utility to investigate sockets.|
|`ps`|Shows process status.|
|`who`|Displays who is logged in.|
|`env`|Prints environment or sets and executes a command.|
|`lsblk`|Lists block devices.|
|`lsusb`|Lists USB devices.|
|`lsof`|Lists opened files.|
|`lspci`|Lists PCI devices.|
|`sudo`|Execute command as a different user.|
|`su`|The `su` utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed.|
|`useradd`|Creates a new user or update default new user information.|
|`userdel`|Deletes a user account and related files.|
|`usermod`|Modifies a user account.|
|`addgroup`|Adds a group to the system.|
|`delgroup`|Removes a group from the system.|
|`passwd`|Changes user password.|
|`dpkg`|Install, remove and configure Debian-based packages.|
|`apt`|High-level package management command-line utility.|
|`aptitude`|Alternative to `apt`.|
|`snap`|Install, remove and configure snap packages.|
|`gem`|Standard package manager for Ruby.|
|`pip`|Standard package manager for Python.|
|`git`|Revision control system command-line utility.|
|`systemctl`|Command-line based service and systemd control manager.|
|`ps`|Prints a snapshot of the current processes.|
|`journalctl`|Query the systemd journal.|
|`kill`|Sends a signal to a process.|
|`bg`|Puts a process into background.|
|`jobs`|Lists all processes that are running in the background.|
|`fg`|Puts a process into the foreground.|
|`curl`|Command-line utility to transfer data from or to a server.|
|`wget`|An alternative to `curl` that downloads files from FTP or HTTP(s) server.|
|`python3 -m http.server`|Starts a Python3 web server on TCP port 8000.|
|`ls`|Lists directory contents.|
|`cd`|Changes the directory.|
|`clear`|Clears the terminal.|
|`touch`|Creates an empty file.|
|`mkdir`|Creates a directory.|
|`tree`|Lists the contents of a directory recursively.|
|`mv`|Move or rename files or directories.|
|`cp`|Copy files or directories.|
|`nano`|Terminal based text editor.|
|`which`|Returns the path to a file or link.|
|`find`|Searches for files in a directory hierarchy.|
|`updatedb`|Updates the locale database for existing contents on the system.|
|`locate`|Uses the locale database to find contents on the system.|
|`more`|Pager that is used to read STDOUT or files.|
|`less`|An alternative to `more` with more features.|
|`head`|Prints the first ten lines of STDOUT or a file.|
|`tail`|Prints the last ten lines of STDOUT or a file.|
|`sort`|Sorts the contents of STDOUT or a file.|
|`grep`|Searches for specific results that contain given patterns.|
|`cut`|Removes sections from each line of files.|
|`tr`|Replaces certain characters.|
|`column`|Command-line based utility that formats its input into multiple columns.|
|`awk`|Pattern scanning and processing language.|
|`sed`|A stream editor for filtering and transforming text.|
|`wc`|Prints newline, word, and byte counts for a given input.|
|`chmod`|Changes permission of a file or directory.|
|`chown`|Changes the owner and group of a file or directory.|

## Regular expresions

**Grouping operators**

|**Operators**|**Description**|
|---|---|---|
|1|`(a)`|The round brackets are used to group parts of a regex. Within the brackets, you can define further patterns which should be processed together.|
|2|`[a-z]`|The square brackets are used to define character classes. Inside the brackets, you can specify a list of characters to search for.|
|3|`{1,10}`|The curly brackets are used to define quantifiers. Inside the brackets, you can specify a number or a range that indicates how often a previous pattern should be repeated.|
|4|`\|`|Also called the OR operator and shows results when one of the two expressions matches|
|5|`.*`|Operates similarly to an AND operator by displaying results only when both expressions are present and match in the specified order|

## File permissions menagement

**chmod**

```bash
Binary Notation:                4 2 1  |  4 2 1  |  4 2 1
----------------------------------------------------------
Binary Representation:          1 1 1  |  1 0 1  |  1 0 0
----------------------------------------------------------
Octal Value:                      7    |    5    |    4
----------------------------------------------------------
Permission Representation:      r w x  |  r - x  |  r - -
```

**chown**

```bash
Fr0g573r@DEDSEC[/htb]$ chown <user>:<group> <file/directory>
```

## Task Scheduling

### Systemd

>1. Create a timer (schedules when your mytimer.service should run)
>2. Create a service (executes the commands or script)
>3. Activate the timer

---
```bash
Zabsooon@htb[/htb]$ sudo mkdir /etc/systemd/system/mytimer.timer.d
Zabsooon@htb[/htb]$ sudo vim /etc/systemd/system/mytimer.timer
```

basic.timer
```shell
[Unit]
Description=My Timer

[Timer]
OnBootSec=3min
OnUnitActiveSec=1hour

[Install]
WantedBy=timers.target
```

---

```bash
Zabsooon@htb[/htb]$ sudo vim /etc/systemd/system/mytimer.service
```

basic.service

```shell
[Unit]
Description=My Service

[Service]
ExecStart=/full/path/to/my/script.sh

[Install]
WantedBy=multi-user.target

```

```bash
Zabsooon@htb[/htb]$ sudo systemctl daemon-reload
Zabsooon@htb[/htb]$ sudo systemctl start mytimer.timer
Zabsooon@htb[/htb]$ sudo systemctl enable mytimer.timer
```

---

### Cron

We can define in a `crontab` scheduled script executions.

|**Time Frame**|**Description**|
|---|---|
|Minutes (0-59)|This specifies in which minute the task should be executed.|
|Hours (0-23)|This specifies in which hour the task should be executed.|
|Days of month (1-31)|This specifies on which day of the month the task should be executed.|
|Months (1-12)|This specifies in which month the task should be executed.|
|Days of the week (0-7)|This specifies on which day of the week the task should be executed.|

## Mounting

If you want a partition to be mounted on system boot you can define it in `/etc/fstab`.

## Dockerization - Docker

### How to install docker-engine

```bash
#!/bin/bash

# Preparation
sudo apt update -y
sudo apt install ca-certificates curl gnupg lsb-release -y
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt update -y
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Add user htb-student to the Docker group
sudo usermod -aG docker htb-student
echo '[!] You need to log out and log back in for the group changes to take effect.'

# Test Docker installation
docker run hello-world
```

### Dockerfile

```bash
# Use the latest Ubuntu 22.04 LTS as the base image
FROM ubuntu:22.04

# Update the package repository and install the required packages
RUN apt-get update && \
    apt-get install -y \
        apache2 \
        openssh-server \
        && \
    rm -rf /var/lib/apt/lists/*

# Create a new user called "docker-user"
RUN useradd -m docker-user && \
    echo "docker-user:password" | chpasswd

# Give the docker-user user full access to the Apache and SSH services
RUN chown -R docker-user:docker-user /var/www/html && \
    chown -R docker-user:docker-user /var/run/apache2 && \
    chown -R docker-user:docker-user /var/log/apache2 && \
    chown -R docker-user:docker-user /var/lock/apache2 && \
    usermod -aG sudo docker-user && \
    echo "docker-user ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Expose the required ports
EXPOSE 22 80

# Start the SSH and Apache services
CMD service ssh start && /usr/sbin/apache2ctl -D FOREGROUND
```

### Docker build

```bash
Zabsooon@htb[/htb]$ docker build -t FS_docker .
```

### Docker run

```bash
Zabsooon@htb[/htb]$ docker run -p <host port>:<docker port> -d <docker container name>
```

```bash
Zabsooon@htb[/htb]$ docker run -p 8022:22 -p 8080:80 -d FS_docker
```

### Docker management

|**Command**|**Description**|
|---|---|
|`docker ps`|List all running containers|
|`docker stop`|Stop a running container.|
|`docker start`|Start a stopped container.|
|`docker restart`|Restart a running container.|
|`docker rm`|Remove a container.|
|`docker rmi`|Remove a Docker image.|
|`docker logs`|View the logs of a container.|

## LXC - Linux Containers

### Installation {#lxc}

```bash
Zabsooon@htb[/htb]$ sudo apt-get install lxc lxc-utils -y
```

### Creating LXC Container

```bash
Zabsooon@htb[/htb]$ sudo lxc-create -n linuxcontainer -t ubuntu
```

### LXC Containers Management

|Command|Description|
|---|---|
|`lxc-ls`|List all existing containers|
|`lxc-stop -n <container>`|Stop a running container.|
|`lxc-start -n <container>`|Start a stopped container.|
|`lxc-restart -n <container>`|Restart a running container.|
|`lxc-config -n <container name> -s storage`|Manage container storage|
|`lxc-config -n <container name> -s network`|Manage container network settings|
|`lxc-config -n <container name> -s security`|Manage container security settings|
|`lxc-attach -n <container>`|Connect to a container.|
|`lxc-attach -n <container> -f /path/to/share`|Connect to a container and share a specific directory or file.|

### Securing LXC

```bash
Zabsooon@htb[/htb]$ sudo vim /usr/share/lxc/config/linuxcontainer.conf
```

```conf
lxc.cgroup.cpu.shares = 512
lxc.cgroup.memory.limit_in_bytes = 512M
```

To apply the changes we need to restart the service:

```bash
Zabsooon@htb[/htb]$ sudo systemctl restart lxc.service
```

### Exercises for later for LXC

| Task | Description |
|---|---|
|1|Install LXC on your machine and create your first container.|
|2|Configure the network settings for your LXC container.|
|3|Create a custom LXC image and use it to launch a new container.|
|4|Configure resource limits for your LXC containers (CPU, memory, disk space).|
|5|Explore the `lxc-*` commands for managing containers.|
|6|Use LXC to create a container running a specific version of a web server (e.g., Apache, Nginx).|
|7|Configure SSH access to your LXC containers and connect to them remotely.|
|8|Create a container with persistence, so changes made to the container are saved and can be reused.|
|9|Use LXC to test software in a controlled environment, such as a vulnerable web application or malware.|

## Linux Networking

### Activate Network Interface

```bash
Zabsooon@htb[/htb]$ sudo ifconfig eth0 up     # OR
Zabsooon@htb[/htb]$ sudo ip link set eth0 up
```

### Assign IP Address to an Interface

```bash
Zabsooon@htb[/htb]$ sudo ifconfig eth0 192.168.1.2
```

### Assign a netmask to an Interface

```bash
Zabsooon@htb[/htb]$ sudo ifconfig eth0 netmask 255.255.255.0
```

### Assign the Route to an Interface

```shell
Zabsooon@htb[/htb]$ sudo route add default gw 192.168.1.1 eth0
```

### DNS Settings

**/etc/resolv.conf**
```bash
nameserver 8.8.8.8
nameserver 8.8.4.4
```

**/etc/network/interfaces**
```bash
auto eth0
iface eth0 inet static
  address 192.168.1.2
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-nameservers 8.8.8.8 8.8.4.4
```

**Restart networking service**

```bash
Zabsooon@htb[/htb]$ sudo systemctl restart networking
```


### System hardening

**SELinux**
| Task | Description |
| --- | ------------------------------------------------------------------------------------------------------------ |
| 1.  | Install SELinux on your VM.                                                                                  |
| 2.  | Configure SELinux to prevent a user from accessing a specific file.                                          |
| 3.  | Configure SELinux to allow a single user to access a specific network service but deny access to all others. |
| 4.  | Configure SELinux to deny access to a specific user or group for a specific network service.                 |

**AppArmor**
| Task | Description |
| --- | ------------------------------------------------------------------------------------------------------------ |
| 5.  | Configure AppArmor to prevent a user from accessing a specific file.                                          |
| 6.  | Configure AppArmor to allow a single user to access a specific network service but deny access to all others. |
| 7.  | Configure AppArmor to deny access to a specific user or group for a specific network service.                 |

**TCP Wrappers**

| Task | Description|
| --- | -------------------------------------------------------------------------------------------------- |
| 8.  | Configure TCP wrappers to allow access to a specific network service from a specific IP address.   |
| 9.  | Configure TCP wrappers to deny access to a specific network service from a specific IP address.    |
| 10. | Configure TCP wrappers to allow access to a specific network service from a range of IP addresses. |

## Remote Desktop

### X11Forwarding

We check if we have **X11Forwarding** *enabled*.

```bash
Zabsooon@htb[/htb]$ cat /etc/ssh/sshd_config | grep X11Forwarding

X11Forwarding yes
```

With this we can start an application remotely.

```bash
Zabsooon@htb[/htb]$ ssh -X htb-student@10.129.23.11 /usr/bin/firefox

htb-student@10.129.14.130's password: ********
<SKIP>
```

### TigerVNC

#### Installation {#tigervnc}

```bash
htb-student@ubuntu:~$ sudo apt install xfce4 xfce4-goodies tigervnc-standalone-server -y
htb-student@ubuntu:~$ vncpasswd 

Password: ******
Verify: ******
Would you like to enter a view-only password (y/n)? n
```

#### Configuration {#tigervnc}

```bash
htb-student@ubuntu:~$ touch ~/.vnc/xstartup ~/.vnc/config
htb-student@ubuntu:~$ cat <<EOT >> ~/.vnc/xstartup

#!/bin/bash
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
/usr/bin/startxfce4
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
x-window-manager &
EOT
```

```bash
htb-student@ubuntu:~$ cat <<EOT >> ~/.vnc/config

geometry=1920x1080
dpi=96
EOT
```

```bash
htb-student@ubuntu:~$ chmod +x ~/.vnc/xstartup
```

#### Start VNCServer

```bash
htb-student@ubuntu:~$ vncserver

New 'linux:1 (htb-student)' desktop at :1 on machine linux

Starting applications specified in /home/htb-student/.vnc/xstartup
Log file is /home/htb-student/.vnc/linux:1.log

Use xtigervncviewer -SecurityTypes VncAuth -passwd /home/htb-student/.vnc/passwd :1 to connect to the VNC server.
```

#### List sessions {#vncserver}

```bash
htb-student@ubuntu:~$ vncserver -list

TigerVNC server sessions:

X DISPLAY #     RFB PORT #      PROCESS ID
:1              5901            79746
```

#### Setting up an SSH Tunel {#vncserver}

```bash
Zabsooon@htb[/htb]$ ssh -L 5901:127.0.0.1:5901 -N -f -l htb-student 10.129.14.130

htb-student@10.129.14.130's password: *******
```

#### Connect to the server {#vncserver}

```bash
Zabsooon@htb[/htb]$ xtightvncviewer localhost:5901

Connected to RFB server, using protocol version 3.8
Performing standard VNC authentication

Password: ******

Authentication successful
Desktop name "linux:1 (htb-student)"
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Same machine: preferring raw encoding
```

## Linux Hardening

### Block traffic

`/etc/hosts.allow`
```bash
Zabsooon@htb[/htb]$ cat /etc/hosts.allow

# Allow access to SSH from the local network
sshd : 10.129.14.0/24

# Allow access to FTP from a specific host
ftpd : 10.129.14.10

# Allow access to Telnet from any host in the inlanefreight.local domain
telnetd : .inlanefreight.local
```

`/etc/hosts.allow`
```bash
Zabsooon@htb[/htb]$ cat /etc/hosts.deny

# Deny access to all services from any host in the inlanefreight.com domain
ALL : .inlanefreight.com

# Deny access to SSH from a specific host
sshd : 10.129.22.22

# Deny access to FTP from hosts with IP addresses in the range of 10.129.22.0 to 10.129.22.255
ftpd : 10.129.22.0/24
```

### Firewall Setup

#### IpTables

|**Component**|**Description**|
|---|---|
|`Tables`|Tables are used to organize and categorize firewall rules.|
|`Chains`|Chains are used to group a set of firewall rules applied to a specific type of network traffic.|
|`Rules`|Rules define the criteria for filtering network traffic and the actions to take for packets that match the criteria.|
|`Matches`|Matches are used to match specific criteria for filtering network traffic, such as source or destination IP addresses, ports, protocols, and more.|
|`Targets`|Targets specify the action for packets that match a specific rule. For example, targets can be used to accept, drop, or reject packets or modify the packets in another way.|

---

#### Tables

|**Table Name**|**Description**|**Built-in Chains**|
|---|---|---|
|`filter`|Used to filter network traffic based on IP addresses, ports, and protocols.|INPUT, OUTPUT, FORWARD|
|`nat`|Used to modify the source or destination IP addresses of network packets.|PREROUTING, POSTROUTING|
|`mangle`|Used to modify the header fields of network packets.|PREROUTING, OUTPUT, INPUT, FORWARD, POSTROUTING|


---

#### Rules and Targets

|**Target Name**|**Description**|
|---|---|
|`ACCEPT`|Allows the packet to pass through the firewall and continue to its destination|
|`DROP`|Drops the packet, effectively blocking it from passing through the firewall|
|`REJECT`|Drops the packet and sends an error message back to the source address, notifying them that the packet was blocked|
|`LOG`|Logs the packet information to the system log|
|`SNAT`|Modifies the source IP address of the packet, typically used for Network Address Translation (NAT) to translate private IP addresses to public IP addresses|
|`DNAT`|Modifies the destination IP address of the packet, typically used for NAT to forward traffic from one IP address to another|
|`MASQUERADE`|Similar to SNAT but used when the source IP address is not fixed, such as in a dynamic IP address scenario|
|`REDIRECT`|Redirects packets to another port or IP address|
|`MARK`|Adds or modifies the Netfilter mark value of the packet, which can be used for advanced routing or other purposes|

---

#### Matches

|**Match Name**|**Description**|
|---|---|
|`-p` or `--protocol`|Specifies the protocol to match (e.g. tcp, udp, icmp)|
|`--dport`|Specifies the destination port to match|
|`--sport`|Specifies the source port to match|
|`-s` or `--source`|Specifies the source IP address to match|
|`-d` or `--destination`|Specifies the destination IP address to match|
|`-m state`|Matches the state of a connection (e.g. NEW, ESTABLISHED, RELATED)|
|`-m multiport`|Matches multiple ports or port ranges|
|`-m tcp`|Matches TCP packets and includes additional TCP-specific options|
|`-m udp`|Matches UDP packets and includes additional UDP-specific options|
|`-m string`|Matches packets that contain a specific string|
|`-m limit`|Matches packets at a specified rate limit|
|`-m conntrack`|Matches packets based on their connection tracking information|
|`-m mark`|Matches packets based on their Netfilter mark value|
|`-m mac`|Matches packets based on their MAC address|
|`-m iprange`|Matches packets based on a range of IP addresses|

---

*Exercises for IpTables*

1.	Launch a web server on TCP/8080 port on your target and use iptables to block incoming traffic on that port.
2.	Change iptables rules to allow incoming traffic on the TCP/8080 port.
3.	Block traffic from a specific IP address.
4.	Allow traffic from a specific IP address.
5.	Block traffic based on protocol.
6.	Allow traffic based on protocol.
7.	Create a new chain.
8.	Forward traffic to a specific chain.
9.	Delete a specific rule.
10.	List all existing rules.

---

### System logs

Logs types:
- Kernel Logs (`/var/log/kern.log`)
- System Logs (`/var/log/syslog`)
- Authentication Logs (`/var/log/auth.log`)
- Application Logs (`/var/log/*app*/error.log`)
- Security Logs


|**Service**|**Description**|
|---|---|
|`Apache`|Access logs are stored in the /var/log/apache2/access.log file (or similar, depending on the distribution).|
|`Nginx`|Access logs are stored in the /var/log/nginx/access.log file (or similar).|
|`OpenSSH`|Access logs are stored in the /var/log/auth.log file on Ubuntu and in /var/log/secure on CentOS/RHEL.|
|`MySQL`|Access logs are stored in the /var/log/mysql/mysql.log file.|
|`PostgreSQL`|Access logs are stored in the /var/log/postgresql/postgresql-version-main.log file.|
|`Systemd`|Access logs are stored in the /var/log/journal/ directory.|

### Shortcuts

**Cursor Movement**

[CTRL] + A - Move the cursor to the beginning of the current line.

[CTRL] + E - Move the cursor to the end of the current line.

[CTRL] + [←] / [→] - Jump at the beginning of the current/previous word.

[ALT] + B / F - Jump backward/forward one word.

---

**Erase The Current Line**

[CTRL] + U - Erase everything from the current position of the cursor to the beginning of the line.

[Ctrl] + K - Erase everything from the current position of the cursor to the end of the line.

[Ctrl] + W - Erase the word preceding the cursor position.

---

**Paste Erased Contents**

[Ctrl] + Y - Pastes the erased text or word.

---

**Ends Task**

[CTRL] + C - Ends the current task/process by sending the SIGINT signal. For example, this can be a scan that is running by a tool. If we are watching the scan, we can stop it / kill this process by using this shortcut. While not configured and developed by the tool we are using. The process will be killed without asking us for confirmation.

---

**End-of-File (EOF)**

[CTRL] + D - Close STDIN pipe that is also known as End-of-File (EOF) or End-of-Transmission.

---

**Clear Terminal**

[CTRL] + L - Clears the terminal. An alternative to this shortcut is the clear command you can type to clear our terminal.

---

**Background a Process**

[CTRL] + Z - Suspend the current process by sending the SIGTSTP signal.

---

**Search Through Command History**

[CTRL] + R - Search through command history for commands we typed previously that match our search patterns.

[↑] / [↓] - Go to the previous/next command in the command history.

---

**Switch Between Applications**

[ALT] + [TAB] - Switch between opened applications.

---

**Zoom**

[CTRL] + [+] - Zoom in.

[CTRL] + [-] - Zoom out.

---

## File Operators {#bash}

|**Operator**|**Description**|
|---|---|
|`-e`|if the file exist|
|`-f`|tests if it is a file|
|`-d`|tests if it is a directory|
|`-L`|tests if it is if a symbolic link|
|`-N`|checks if the file was modified after it was last read|
|`-O`|if the current user owns the file|
|`-G`|if the file’s group id matches the current user’s|
|`-s`|tests if the file has a size greater than 0|
|`-r`|tests if the file has read permission|
|`-w`|tests if the file has write permission|
|`-x`|tests if the file has execute permission|

## Return Codes {#bash}


|**Return Code**|**Description**|
|---|---|
|`1`|General errors|
|`2`|Misuse of shell builtins|
|`126`|Command invoked cannot execute|
|`127`|Command not found|
|`128`|Invalid argument to exit|
|`128+n`|Fatal error signal "`n`"|
|`130`|Script terminated by Control-C|
|`255\*`|Exit status out of range|

## Windows Cheatsheet

|**Command**|**Description**|
|---|---|
|`xfreerdp /v:<target IP address> /u:htb-student /p:<password>`|RDP to lab target|
|`Get-WmiObject -Class win32_OperatingSystem`|Get information about the operating system|
|`dir c:\ /a`|View all files and directories in the c:\ root directory|
|`tree <directory>`|Graphically displaying the directory structure of a path|
|`tree c:\ /f \| more`|Walk through results of the `tree` command page by page|
|`icacls <directory>`|View the permissions set on a directory|
|`icacls c:\users /grant joe:f`|Grant a user full permissions to a directory|
|`icacls c:\users /remove joe`|Remove a users' permissions on a directory|
|`Get-Service`|`PowerShell` cmdlet to view running services|
|`help <command>`|Display the help menu for a specific command|
|`get-alias`|List `PowerShell` aliases|
|`New-Alias -Name "Show-Files" Get-ChildItem`|Create a new `PowerShell` alias|
|`Get-Module \| select Name,ExportedCommands \| fl`|View imported `PowerShell` modules and their associated commands|
|`Get-ExecutionPolicy -List`|View the `PowerShell` execution policy|
|`Set-ExecutionPolicy Bypass -Scope Process`|Set the `PowerShell` execution policy to bypass for the current session|
|`wmic os list brief`|Get information about the operating system with `wmic`|
|`Invoke-WmiMethod`|Call methods of `WMI` objects|
|`whoami /user`|View the current users' SID|
|`reg query <key>`|View information about a registry key|
|`Get-MpComputerStatus`|Check which `Defender` protection settings are enabled|
|`sconfig`|Load Server Configuration menu in Windows Server Core|

## Creating a Network Share {#windows}

Basicly you go to `properties` of folder on the system, you go to `sharing`, next `advanced sharing`, you enable sharing the folder by clicking `Share this folder`.
You can add permissions for accessing the folder for the user by clicking `Permissions`.

## Connecting to Network Share {#windows}

List available shares:

```bash
Zabsooon@htb[/htb]$ smbclient -L SERVER_IP -U htb-student
Enter WORKGROUP\htb-student's password: 

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    Company Data    Disk      
    IPC$            IPC       Remote IPC
```

Connecting to company data share:

```bash
Zabsooon@htb[/htb]$ smbclient '\\SERVER_IP\Company Data' -U htb-student
Password for [WORKGROUP\htb-student]:
Try "help" to get a list of possible commands.

smb: \>
```

## Windows Execution Policy

|**Policy**|**Description**|
|---|---|
|`AllSigned`|All scripts can run, but a trusted publisher must sign scripts and configuration files. This includes both remote and local scripts. We receive a prompt before running scripts signed by publishers that we have not yet listed as either trusted or untrusted.|
|`Bypass`|No scripts or configuration files are blocked, and the user receives no warnings or prompts.|
|`Default`|This sets the default execution policy, `Restricted` for Windows desktop machines and `RemoteSigned` for Windows servers.|
|`RemoteSigned`|Scripts can run but requires a digital signature on scripts that are downloaded from the internet. Digital signatures are not required for scripts that are written locally.|
|`Restricted`|This allows individual commands but does not allow scripts to be run. All script file types, including configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`) are blocked.|
|`Undefined`|No execution policy is set for the current scope. If the execution policy for ALL scopes is set to undefined, then the default execution policy of `Restricted` will be used.|
|`Unrestricted`|This is the default execution policy for non-Windows computers, and it cannot be changed. This policy allows for unsigned scripts to be run but warns the user before running scripts that are not from the local intranet zone.|

## Windows Fundamentals - Skills Assessment

TBD :)

---

## Exercises

**Here I put all of the exercises and what commands I executed to solve them**.

---

*What is the name of the config file that has been created after 2020-03-03 and is smaller than 28k but larger than 25k?*

```bash
find / -type f -name *.conf -size +25k -size -28k -exec ls -al {} \; 2>/dev/null
```

You can check man page but here is what this describes:

|**Option**|**Description**|
|---|---|
|`-type f`|Hereby, we define the type of the searched object. In this case, '`f`' stands for '`file`'.|
|`-name *.conf`|With '`-name`', we indicate the name of the file we are looking for. The asterisk (`*`) stands for 'all' files with the '`.conf`' extension.|
|`-user root`|This option filters all files whose owner is the root user.|
|`-size +20k`|We can then filter all the located files and specify that we only want to see the files that are larger than 20 KiB.|
|`-newermt 2020-03-03`|With this option, we set the date. Only files newer than the specified date will be presented.|
|`-exec ls -al {} \;`|This option executes the specified command, using the curly brackets as placeholders for each result. The backslash escapes the next character from being interpreted by the shell because otherwise, the semicolon would terminate the command and not reach the redirection.|
|`2>/dev/null`|This is a `STDERR` redirection to the '`null device`', which we will come back to in the next section. This redirection ensures that no errors are displayed in the terminal. This redirection must `not` be an option of the 'find' command.|

---

*Use cURL from your Pwnbox (not the target machine) to obtain the source code of the "https://www.inlanefreight.com" website and filter all unique paths (https://www.inlanefreight.com/directory" or "/another/directory") of that domain. Submit the number of these paths as the answer.*

```bash
curl "https://www.inlanefreight.com/" | grep -Po "https://www.inlanefreight.com/[^\"' >]*" | sort -u | wc -l
```

---
