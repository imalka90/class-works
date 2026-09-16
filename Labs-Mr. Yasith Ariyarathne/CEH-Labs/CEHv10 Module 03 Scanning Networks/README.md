# Module 03: Network Scanning and Host Discovery Labs

This repository contains practical laboratory documentation, procedure logs, and analysis covering **Module 03: Scanning Networks**. These labs demonstrate techniques used by security professionals to detect live hosts, craft custom packets, perform service/OS auditing, map network topologies, and implement firewall evasion strategies.

---

# Network Scanning & Enumeration Lab Series — Index

1. [Lab 1 Scanning the Network using the Colasoft Packet Builder](#lab-1-scanning-the-network-using-the-colasoft-packet-builder) — [View Lab](./Lab%2001%20Scanning%20the%20Network%20using%20the%20Colasoft%20Packet%20Builder/)
2. [Lab 2 UDP and TCP Packet Crafting Techniques using HPING3](#lab-2-udp-and-tcp-packet-crafting-techniques-using-hping3) — [View Lab](./Lab%2002%20UDP%20and%20TCP%20Packet%20Crafting%20Techniques%20using%20HPING3/)
3. [Lab 3 Basic Network Troubleshooting using MegaPing](#lab-3-basic-network-troubleshooting-using-megaping) — [View Lab](./Lab%2003%20Basic%20Network%20Troubleshooting%20using%20MegaPing/)
4. [Lab 4 Understanding Network Scanning using Nmap](#lab-4-understanding-network-scanning-using-nmap) — [View Lab](./Lab%2004%20Understanding%20Network%20Scanning%20using%20Nmap/)
5. [Lab 5 Scanning a Network using NetScan Tools Pro](#lab-5-scanning-a-network-using-netscan-tools-pro) — [View Lab](./Lab%2005%20Scanning%20a%20Network%20using%20NetScan%20Tools%20Pro/)


---


## Technical Overview & Environment Requirements

* **Primary Attacker Systems:** Kali Linux (hping3, Nmap, ProxyChains), Windows Server 2016 / Windows 10 (GUI utilities)
* **Target Environment:** Multi-OS Network (Windows Server 2012/2016, Windows 10, Ubuntu Linux)
* **Core Toolsets:** Colasoft Packet Builder, HPING3, MegaPing, Nmap/Zenmap, NetScanTools Pro, Angry IP Scanner, ID Serve, CurrPorts, The Dude, Friendly Pinger, Nessus, ProxyChains.

---

## Comprehensive Lab Index

### Lab 1: Scanning the Network using Colasoft Packet Builder
* **Topic:** Live Host Detection via ARP Ping Scanning
* **Objective:** Construct custom ARP Request packets and send them via broadcast/burst mode to discover active IP/MAC pairings on the local subnet.
* **Core Steps:**
  * Select the local active Network Adapter.
  * Construct an ARP Request frame using standard template definitions (Delta time: 0.1s).
  * Configure **Burst Mode** to rapidly transmit the probe across the segment.
  * Capture returning unicast ARP responses via Wireshark or Colasoft Packet Capture.

### Lab 2: UDP and TCP Packet Crafting Techniques using HPING3
* **Topic:** Custom Packet Crafting, SYN Scans, and UDP Probing
* **Objective:** Craft custom transport layer frames to perform custom port scans, send fragmented probes, and test host response capabilities.
* **Core Commands & Options:**
  * **Basic ICMP Ping Probing:** `hping3 -c 3 <Target IP>`
  * **SYN Port Range Scan:** `hping3 --scan 1-3000 -S <Target IP>`
  * **UDP Flooding / Payload Insertion:** `hping3 <Target IP> --udp --rand-source --data 500`
  * **Explicit Port SYN Probe:** `hping3 -S <Target IP> -p 80 -c 5`
  * **SYN Flood Simulation:** `hping3 <Target IP> --flood`

### Lab 3: Basic Network Troubleshooting using MegaPing
* **Topic:** Host Discovery, Port Scanning, and Service Identification
* **Objective:** Execute full-range IP sweeps and port audits on Windows target systems using an integrated GUI toolkit.
* **Core Steps:**
  * Run the **IP Scanner** utility against an IP range (e.g., `10.10.10.1` to `10.10.10.50`) to evaluate live status and TTL responses.
  * Perform a target **Traceroute** to measure network hop distance.
  * Execute a **Port Scan** on designated active targets to identify open listening ports, service risk levels, and protocols.

### Lab 4: Understanding Network Scanning using Nmap
* **Topic:** Subnet Exploration, OS Detection, and Packet Tracing
* **Objective:** Gain command-line and graphical scanning proficiency to map active subnets and inspect raw probe behavior.
* **Core Scans:**
  * **Subnet Exploration:** `nmap 10.10.10.*` (Scans full `/24` block for active hosts).
  * **Packet Trace Debugging:** `nmap --packet-trace <Target IP>` (Displays step-by-step sent/received frame details).
  * **Slow Comprehensive Scan:** `nmap -sS -sU -T4 -A -v -PE -PP -PS80,443 -PA3389 -PU40125 -PY -g 53 --script "default or (discovery and safe)" <Target IP>`
  * **Null Scan Profile Creation:** `nmap -sN -T4 -A <Target IP>` (Sends TCP frames with no control flags set to bypass RFC 793 compliant systems).

### Lab 5: Scanning a Network using NetScanTools Pro
* **Topic:** Subnet Sweeping (ARP/MAC Scan) and DHCP Server Discovery
* **Objective:** Gather internal subnet infrastructure parameters using automated diagnostic tools.
* **Core Steps:**
  * Perform **ARP Ping** and **ARP Scan (MAC Scan)** across local IP ranges to resolve IP-to-MAC associations.
  * Launch **DHCP Server Discovery** to identify active or unauthorized (rogue) DHCP servers on the local LAN segment.
  * Execute **Ping Scans** to verify operational host availability.
  

# Lab 06: Scanning for Network Traffic Going through a Computer's Adapter using IP-Tools

* **Topic:** Adapter Statistics, Live Traffic Monitoring, and Network Host/Port Discovery
* **Objective:** Monitor network interface metrics, observe real-time packet throughput, and audit active host entry points using IP-Tools.
* **Core Steps:**
  * Install and launch **IP-Tools** with administrative privileges.
  * Access **Adapter Statistics** to track bandwidth consumption, active interface metrics, and real-time packet flow.
  * Execute **Ping Scans** and **Port Scans** across target IP ranges to detect live operational hosts and listening network services.




---








