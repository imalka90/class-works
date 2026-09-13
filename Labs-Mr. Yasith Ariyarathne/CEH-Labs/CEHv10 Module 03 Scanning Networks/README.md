# Module 03: Network Scanning and Host Discovery Labs

This repository contains practical laboratory documentation, procedure logs, and analysis covering **Module 03: Scanning Networks**. These labs demonstrate techniques used by security professionals to detect live hosts, craft custom packets, perform service/OS auditing, map network topologies, and implement firewall evasion strategies.

---

# Network Scanning & Enumeration Lab Series — Index

1. [Lab 1 Scanning the Network using the Colasoft Packet Builder](#lab-1-scanning-the-network-using-the-colasoft-packet-builder) — [View Lab](./Lab%201%20Scanning%20the%20Network%20using%20the%20Colasoft%20Packet%20Builder/)
2. [Lab 2 UDP and TCP Packet Crafting Techniques using HPING3](#lab-2-udp-and-tcp-packet-crafting-techniques-using-hping3) — [View Lab](./Lab%202%20UDP%20and%20TCP%20Packet%20Crafting%20Techniques%20using%20HPING3/)
3. [Lab 3 Basic Network Troubleshooting using MegaPing](#lab-3-basic-network-troubleshooting-using-megaping) — [View Lab](./Lab%203%20Basic%20Network%20Troubleshooting%20using%20MegaPing/)
4. [Lab 4 Understanding Network Scanning using Nmap](#lab-4-understanding-network-scanning-using-nmap) — [View Lab](./Lab%204%20Understanding%20Network%20Scanning%20using%20Nmap/)
5. [Lab 5 Scanning a Network using NetScan Tools Pro](#lab-5-scanning-a-network-using-netscan-tools-pro) — [View Lab](./Lab%205%20Scanning%20a%20Network%20using%20NetScan%20Tools%20Pro/)
6. [Lab 6 Host Discovery using Angry IP Scanner](#lab-6-host-discovery-using-angry-ip-scanner) — [View Lab](./Lab%206%20Host%20Discovery%20using%20Angry%20IP%20Scanner/)
7. [Lab 7 OS Discovery and Banner Grabbing using Zenmap](#lab-7-os-discovery-and-banner-grabbing-using-zenmap) — [View Lab](./Lab%207%20OS%20Discovery%20and%20Banner%20Grabbing%20using%20Zenmap/)
8. [Lab 8 Banner Grabbing using Telnet and ID Serve](#lab-8-banner-grabbing-using-telnet-and-id-serve) — [View Lab](./Lab%208%20Banner%20Grabbing%20using%20Telnet%20and%20ID%20Serve/)
9. [Lab 9 Monitoring Active TCP/IP Connections using CurrPorts](#lab-9-monitoring-active-tcpip-connections-using-currports) — [View Lab](./Lab%209%20Monitoring%20Active%20TCP%2FIP%20Connections%20using%20CurrPorts/)
10. [Lab 10 Network Topology Mapping using The Dude](#lab-10-network-topology-mapping-using-the-dude) — [View Lab](./Lab%2010%20Network%20Topology%20Mapping%20using%20The%20Dude/)
11. [Lab 11 Network Monitoring and Mapping using Friendly Pinger](#lab-11-network-monitoring-and-mapping-using-friendly-pinger) — [View Lab](./Lab%2011%20Network%20Monitoring%20and%20Mapping%20using%20Friendly%20Pinger/)
12. [Lab 12 Firewall/IDS Evasion using Nmap Packet Fragmentation](#lab-12-firewallids-evasion-using-nmap-packet-fragmentation) — [View Lab](./Lab%2012%20Firewall%2FIDS%20Evasion%20using%20Nmap%20Packet%20Fragmentation/)
13. [Lab 13 Firewall/IDS Evasion using Nmap IP Decoys and MAC Spoofing](#lab-13-firewallids-evasion-using-nmap-ip-decoys-and-mac-spoofing) — [View Lab](./Lab%2013%20Firewall%2FIDS%20Evasion%20using%20Nmap%20IP%20Decoys%20and%20MAC%20Spoofing/)
14. [Lab 14 Vulnerability Assessment using Nessus](#lab-14-vulnerability-assessment-using-nessus) — [View Lab](./Lab%2014%20Vulnerability%20Assessment%20using%20Nessus/)
15. [Lab 15 Anonymizing Network Scans via ProxyChains](#lab-15-anonymizing-network-scans-via-proxychains) — [View Lab](./Lab%2015%20Anonymizing%20Network%20Scans%20via%20ProxyChains/)


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

### Lab 6: Host Discovery using Angry IP Scanner
* **Topic:** Fast Multi-Threaded Ping Sweeps and Host Reachability
* **Objective:** Conduct rapid, lightweight IP range discovery across massive address blocks using multi-threaded ICMP/port probes.
* **Core Steps:**
  * Define target range and netmask parameters.
  * Configure multi-threaded fetchers (IP, Hostname, Ping time, Open Ports).
  * Analyze green (live host) vs. red (dead host) outputs and export reports.

### Lab 7: OS Discovery and Banner Grabbing using Zenmap
* **Topic:** GUI-Based OS Fingerprinting and Service Version Auditing
* **Objective:** Determine target Operating System versions and daemon releases via active probe interrogation.
* **Core Steps:**
  * Execute **OS Detection (`nmap -O`)** and **Service Version Detection (`nmap -sV`)**.
  * Examine TCP/IP stack implementation responses (TTL values, Window Size, TCP Options).
  * Review the Zenmap **Topology Graph** and **Host Details** panes to document infrastructure specs.

### Lab 8: Banner Grabbing using Telnet and ID Serve
* **Topic:** Direct Application Protocol Interrogation and Web Server Banner Analysis
* **Objective:** Retrieve exact service version banners from target web servers and remote access services without generating automated scanner signatures.
* **Core Steps:**
  * Connect via command-line Telnet to raw ports: `telnet <Target IP> 80` followed by `HEAD / HTTP/1.0`.
  * Run **ID Serve** against target URLs/IP addresses to extract `Server:`, `X-Powered-By:`, and underlying framework details.

### Lab 9: Monitoring Active TCP/IP Connections using CurrPorts
* **Topic:** Local Listening Ports, PID Tracking, and Process-to-Port Mapping
* **Objective:** Monitor active local endpoints to detect unauthorized connections, backdoors, or open listening services.
* **Core Steps:**
  * Launch CurrPorts to map local listening/established TCP & UDP ports to their exact Process ID (PID) and process path.
  * Inspect remote target IP addresses, port associations, and connection states (`LISTEN`, `ESTABLISHED`).
  * Terminate suspicious processes directly from the port mapping interface.

### Lab 10: Network Topology Mapping using The Dude
* **Topic:** Automated Network Discovery and Dynamic Visual Topology Creation
* **Objective:** Automatically map network infrastructure and build real-time monitoring diagrams.
* **Core Steps:**
  * Configure network discovery range specifications and device probe types (SNMP, Ping, HTTP).
  * Execute automated dynamic network layout rendering.
  * Monitor real-time status changes and link latency indicators across mapped nodes.

### Lab 11: Network Monitoring and Mapping using Friendly Pinger
* **Topic:** Visual Host Polling and Network Layout Management
* **Objective:** Build custom visual maps of network infrastructure with integrated availability polling.
* **Core Steps:**
  * Create custom device maps representing routers, switches, servers, and workstations.
  * Configure ICMP/TCP ping intervals to continuously audit host reachability.
  * Set up visual/auditory alerts for host failures and link disconnects.

### Lab 12: Firewall/IDS Evasion using Nmap Packet Fragmentation
* **Topic:** Bypassing Deep Packet Inspection via Fragmented Probes
* **Objective:** Split probe payloads into smaller fragments to bypass simple packet inspection rules and non-reassembling firewalls.
* **Core Commands:**
  * **Standard Fragmented Scan:** `nmap -f <Target IP>` (Splits header into 8-byte fragments).
  * **Custom MTU Scan:** `nmap --mtu 16 <Target IP>` (Splits packets into specified offset multiples).

### Lab 13: Firewall/IDS Evasion using Nmap IP Decoys and MAC Spoofing
* **Topic:** Source Obfuscation via Decoy IP Addresses and Spoofed Ethernet Hardware Addresses
* **Objective:** Obfuscate scan source identity by blending real traffic with false decoy addresses and custom Ethernet MAC addresses.
* **Core Commands:**
  * **IP Decoy Scan:** `nmap -D RND:10 <Target IP>` or `nmap -D DecoyIP1,DecoyIP2,ME <Target IP>`
  * **MAC Address Spoofing:** `nmap --spoof-mac 0 <Target IP>` (Randomized MAC) or `nmap --spoof-mac Apple <Target IP>`

### Lab 14: Vulnerability Assessment using Nessus
* **Topic:** Automated Network Vulnerability Scanning and CVE Identification
* **Objective:** Perform complete vulnerability audits against target hosts to identify unpatched software, weak configurations, and known CVE exposures.
* **Core Steps:**
  * Configure **Basic Network Scan** policies targeting active IP blocks.
  * Execute authenticated/unauthenticated scanning profiles.
  * Categorize scan findings by severity (**Info, Low, Medium, High, Critical**) and cross-reference CVE IDs.

### Lab 15: Anonymizing Network Scans via ProxyChains
* **Topic:** Multi-Hop Traffic Proxification and IP Anonymization
* **Objective:** Route command-line port scanning and probing tools through TOR or chained SOCKS4/SOCKS5/HTTP proxies to obscure source identity.
* **Core Steps:**
  * Configure dynamic/strict proxy chains within `/etc/proxychains.conf`.
  * Append public/private SOCKS4/SOCKS5 server lists.
  * Execute scans through the chain: `proxychains nmap -sT -pn -n <Target IP>`

---

## Lab Verification Checklist

| Lab # | Technique / Target Focus | Core Tool | Status | Verification Method |
| :--- | :--- | :--- | :--- | :--- |
| **Lab 01** | Layer 2 ARP Sweeping | Colasoft Packet Builder | Completed | Wireshark ARP Reply Log |
| **Lab 02** | Transport Layer Packet Crafting | HPING3 | Completed | Wireshark Packet Capture |
| **Lab 03** | Multi-utility Host Audit | MegaPing | Completed | GUI Security Scan Report |
| **Lab 04** | Subnet Scanning & Trace | Nmap / Zenmap | Completed | Console Output / Topology View |
| **Lab 05** | ARP & DHCP Server Audit | NetScanTools Pro | Completed | Responding DHCP List |
| **Lab 06** | Fast Multi-threaded Ping Sweep | Angry IP Scanner | Completed | Host Reachability Output |
| **Lab 07** | OS Fingerprinting & Services | Zenmap | Completed | OS & Service Version Matrix |
| **Lab 08** | Banner Grabbing | Telnet / ID Serve | Completed | Web Server HTTP Headers |
| **Lab 09** | Local Port-to-PID Mapping | CurrPorts | Completed | Process Connection Table |
| **Lab 10** | Dynamic Network Discovery | The Dude | Completed | Generated Topology Map |
| **Lab 11** | Host Polling & Layout | Friendly Pinger | Completed | Visual Map & Ping Status |
| **Lab 12** | DPI Evasion via Fragmentation | Nmap (`-f` / `--mtu`) | Completed | Fragmented Capture Analysis |
| **Lab 13** | Source Identity Obfuscation | Nmap (`-D` / `--spoof-mac`) | Completed | Target Log Inspection |
| **Lab 14** | CVE Vulnerability Assessment | Nessus | Completed | Vulnerability Severity Report |
| **Lab 15** | Proxified Multi-hop Scanning | ProxyChains | Completed | Chain Routing Output Log |




---

