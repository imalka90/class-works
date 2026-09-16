# Module 03: Network Scanning and Host Discovery Labs

This repository contains practical laboratory documentation, procedure logs, and analysis covering **Module 03: Scanning Networks**. These labs demonstrate techniques used by security professionals to detect live hosts, craft custom packets, perform service/OS auditing, map network topologies, and implement firewall evasion strategies.

---

# Network Scanning & Enumeration Lab Series — Index

1. [Lab 1 Scanning the Network using the Colasoft Packet Builder](#lab-1-scanning-the-network-using-the-colasoft-packet-builder) — [View Lab](./Lab%2001%20Scanning%20the%20Network%20using%20the%20Colasoft%20Packet%20Builder/)
2. [Lab 2 UDP and TCP Packet Crafting Techniques using HPING3](#lab-2-udp-and-tcp-packet-crafting-techniques-using-hping3) — [View Lab](./Lab%2002%20UDP%20and%20TCP%20Packet%20Crafting%20Techniques%20using%20HPING3/)
3. [Lab 3 Basic Network Troubleshooting using MegaPing](#lab-3-basic-network-troubleshooting-using-megaping) — [View Lab](./Lab%2003%20Basic%20Network%20Troubleshooting%20using%20MegaPing/)
4. [Lab 4 Understanding Network Scanning using Nmap](#lab-4-understanding-network-scanning-using-nmap) — [View Lab](./Lab%2004%20Understanding%20Network%20Scanning%20using%20Nmap/)
5. [Lab 5 Scanning a Network using NetScan Tools Pro](#lab-5-scanning-a-network-using-netscan-tools-pro) — [View Lab](./Lab%2005%20Scanning%20a%20Network%20using%20NetScan%20Tools%20Pro/)
6. [Lab 6 Scanning for Network Traffic Going through a Computer's Adapter using IP-Tools](#lab-6-scanning-for-network-traffic-going-through-a-computers-adapter-using-ip-tools) — [View Lab](./Lab%2006%20Scanning%20for%20Network%20Traffic%20Going%20through%20a%20Computer's%20Adapter%20using%20IP-Tools/)
7. [Lab 7 Checking for Live Systems using Angry IP Scanner](#lab-7-checking-for-live-systems-using-angry-ip-scanner) — [View Lab](./Lab%2007%20Checking%20for%20Live%20Systems%20using%20Angry%20IP%20Scanner/)
8. [Lab 8 Exploring Various Network Scanning Techniques](#lab-8-exploring-various-network-scanning-techniques) — [View Lab](./Lab%2008%20Exploring%20Various%20Network%20Scanning%20Techniques/)
9. [Lab 09 Perform ICMP Probing using PingTraceroute for Network Troubleshooting](#lab-09-firewalls-intrusion-detection-systems-ids-and-evasion-techniques) — [View Lab](./Lab%2009%20Perform%20ICMP%20Probing%20using%20PingTraceroute%20for%20Network%20Troubleshooting/)
10. [Lab 10 Avoiding Scanning Detection using Multiple Decoy IP Addresses](#lab-10-avoiding-scanning-detection-using-multiple-decoy-ip-addresses) — [View Lab](./Lab%2010%20Avoiding%20Scanning%20Detection%20using%20Multiple%20Decoy%20IP%20Addresses/)
11. [Lab 11 Daisy Chaining using Proxy Workbench](#lab-11-daisy-chaining-using-proxy-tools) — [View Lab](./Lab%2011%20Daisy%20Chaining%20using%20Proxy%20Workbench/)
12. [Lab 12 Anonymous Browsing using Proxy Switcher](#lab-12-anonymous-browsing-using-proxy-switcher) — [View Lab](./Lab%2012%20Anonymous%20Browsing%20using%20Proxy%20Switcher/)
13. [Lab 13 Anonymous Browsing using CyberGhost](#lab-13-anonymous-browsing-using-cyberghost) — [View Lab](./Lab%2013%20Anonymous%20Browsing%20using%20CyberGhost/)

14. [Lab 14 Identify Target System's OS with Time-to-Live (TTL) and TCP Window Sizes using Wireshark](#lab-14-identify-target-systems-os-with-time-to-live-ttl-and-tcp-window-sizes-using-wireshark) — [View Lab](./Lab%2014%20Identify%20Target%20System's%20OS%20with%20Time-to-Live%20(TTL)%20and%20TCP%20Window%20Sizes%20using%20Wireshark/)

15. [Lab 15: Drawing Network Diagrams using Network Topology Mapper](#lab-15-drawing-network-diagrams-using-network-topology-mapper) — [View Lab](./Lab%2015%20Drawing%20Network%20Diagrams%20using%20Network%20Topology%20Mapper/)
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
  

### Lab 06: Scanning for Network Traffic Going through a Computer's Adapter using IP-Tools

* **Topic:** Adapter Statistics, Live Traffic Monitoring, and Network Host/Port Discovery
* **Objective:** Monitor network interface metrics, observe real-time packet throughput, and audit active host entry points using IP-Tools.
* **Core Steps:**
  * Install and launch **IP-Tools** with administrative privileges.
  * Access **Adapter Statistics** to track bandwidth consumption, active interface metrics, and real-time packet flow.
  * Execute **Ping Scans** and **Port Scans** across target IP ranges to detect live operational hosts and listening network services.

### Lab 07: Checking for Live Systems using Angry IP Scanner
* **Topic:** Multi-threaded Subnet Sweeping, Hostname Resolution, and Host Fetcher Inspection
* **Objective:** Perform rapid IP reachability sweeps, map active hosts, and inspect target system metadata using Angry IP Scanner.
* **Core Steps:**
  * Configure the IP scan range (`192.168.45.0` to `192.168.45.255`) and set display preferences to filter for alive hosts.
  * Execute a multi-threaded subnet ping sweep to identify active IP addresses, hostnames, and listening ports.
  * Inspect individual target **Host Details** and fetcher plugins to analyze latency, MAC address vendor metadata, and web server banners.

### Lab 08: Exploring Various Network Scanning Techniques
* **Topic:** Advanced Nmap Port Scanning Techniques, TCP Flag Manipulation, and Firewall Evasion Analysis
* **Objective:** Perform advanced port scans (TCP Connect, Xmas, and ACK Flag scans) using Nmap to analyze target service responses and evaluate the impact of host firewall configurations.
* **Core Steps:**
  * Execute an aggressive **TCP Connect Scan** (`-sT -A`) against the target to gather OS, service versions, and SMB metadata.
  * Enable the target host firewall and run an **Xmas Scan** (`-sX -v -T4`) to analyze RFC 793 packet-filtering behavior.
  * Disable the target firewall and run an **ACK Flag Scan** (`-sA -v -T4`) to verify stateful filtering rule statuses and unfiltered ports.

### Lab 09: Firewalls, Intrusion Detection Systems (IDS), and Evasion Techniques
* **Topic:** Perimeter Defense Bypassing, Port Scanning Strategy, and Network Traffic Evasion Analysis
* **Objective:** Assess firewall filtering behavior and evaluate techniques for discovering active hosts and open services when perimeter controls block standard network probes.
* **Core Steps:**
  * Configure perimeter firewall rules on the target machine to block ICMP echo requests and standard SYN port scanning probes.
  * Perform host discovery using alternative TCP SYN/ACK ping probes (`-PS`, `-PA`) to identify active network hosts through stateful filters.
  * Execute service enumeration utilizing fragmented and protocol-specific probes to analyze rule matching and signature detection limitations.

### Lab 10: Avoiding Scanning Detection using Multiple Decoy IP Addresses
* **Topic:** IP Packet Fragmentation, Custom MTU Customization, and Decoy Source IP Address Spoofing
* **Objective:** Conceal network scanning traffic and evade firewall/IDS detection mechanisms using Nmap packet manipulation and source IP obfuscation.
* **Core Steps:**
  * Enable Windows Defender Firewall on the target host (`192.168.45.131`) across Domain, Private, and Public network profiles
  * Execute an IP fragmentation scan (`nmap -f 192.168.45.131`) and a custom MTU scan (`nmap --mtu 8 192.168.45.131`) from Kali Linux (`192.168.45.128`) to bypass stateful packet inspection signatures
  * Launch a decoy scan (`nmap -D RND:10 192.168.45.131`) and capture incoming traffic in Wireshark to verify spoofed source IP address generation.

### Lab 11: Daisy Chaining using Proxy Tools
* **Topic:** Proxy Daisy Chaining, Intermediate Hop Routing, and Source IP Anonymization

* **Objective:** Conceal network scanning and browsing traffic by routing requests through intermediate proxy nodes using CCProxy and ProxyChains-ng to evade perimeter attribution and direct logging.

* **Core Steps:**

  * Install and configure CCProxy on the Windows host (192.168.45.131) listening on HTTP port 8080, verifying active socket binding with netstat -ano | findstr 8080

  * Configure system-wide manual proxy settings in Google Chrome on the host machine to point to 127.0.0.1:8080

  * Configure /etc/proxychains4.conf on Kali Linux (192.168.45.128) with strict_chain mode and add http 192.168.45.131 8080 under the [ProxyList] section

  * Execute proxy-routed HTTP requests (proxychains4 curl -I [http://google.com](http://google.com)) from Kali Linux and verify active ESTABLISHED TCP connections across the proxy chain via Windows netstat and CCProxy logs.




### Lab 12: Anonymous Browsing using Proxy Switcher
* **Topic:** Automated Proxy Discovery, Latency Testing, and Dynamic IP Anonymization

* **Objective:** Use Proxy Switcher to automatically discover, test, and switch between high-anonymity proxy servers to mask the host's real IP address and maintain internet anonymity during security assessments.

* **Core Steps:**

  * Install and launch Proxy Switcher on the Windows system, opening the application with administrative privileges from the setup wizard or start menu.

  * Configure automatic proxy downloading or import active proxy lists into Proxy Switcher, initiating real-time connectivity and latency testing across the retrieved proxy servers.

  * Select an active high-anonymity proxy server from the tested list and click Switch to Selected Proxy to route all outgoing web traffic through the proxy node.

  * Open a web browser, navigate to an IP-checking site (such as whatismyip.com), and verify that the real host IP address is successfully hidden and replaced by the proxy server's IP address.

### Lab 13 Anonymous Browsing using CyberGhost

* **Topic:** System-Wide VPN Anonymization, Server Node Selection, and Encrypted Tunneling

* **Objective:** Use CyberGhost to automatically connect to secure VPN servers, encrypt system-wide web traffic, and mask the host's real IP address to maintain internet anonymity during security assessments.

* **Core Steps:**

  * Install and launch CyberGhost on the Windows system, opening the application with administrative privileges from the setup wizard or start menu or tool directory (C:\Users\Administrator\Downloads\CyberGhost).

  * Configure anonymity settings and select the desired connection mode (such as Surf Anonymously or Unblock Streaming) alongside choosing a specific country or server node.

  * Click the Connect button to establish an encrypted and secure VPN tunnel, routing all system web traffic through the CyberGhost network.

  * Open a web browser, navigate to an IP-checking site (such as whatismyip.com), and verify that the real host IP address and geographic location are successfully hidden and replaced by the assigned CyberGhost server details.



### Lab 14: Identify Target System's OS with Time-to-Live (TTL) and TCP Window Sizes using Wireshark
* **Topic**: Passive OS Fingerprinting, IP Header Analysis, and TCP Window Size Inspection

* **Objective:** Use Wireshark to capture network packets, inspect Time-to-Live (TTL) and TCP window size fields in IP/TCP headers, and identify the operating system of a target system during security assessments.

* **Core Steps:**

  * Launch Wireshark with administrative privileges on the Windows system and start packet capture on the active network interface.

  * Generate network traffic to the target system (such as Windows Server 2016, Windows 10, or an Ubuntu VM) and use capture filters in Wireshark to isolate traffic originating from the target machine.

  * Inspect the initial packets of a TCP session, expanding the Internet Protocol header to examine the Time-to-Live (TTL) value and the Transmission Control Protocol section to check the TCP Window Size.

  * Correlate the observed TTL and window size values against known OS fingerprinting signatures (such as TTL 128 for Windows or TTL 64 for Linux) to accurately identify the target system's operating system.

### Lab 15: Drawing Network Diagrams using Network Topology Mapper
* **Topic:** Automated Network Discovery, Layer 2/3 Topology Mapping, and Visual Diagram Generation

* **Objective:** Use SolarWinds Network Topology Mapper (NTM) to discover network devices within target subnets, correlate Layer 2 and Layer 3 topology data using SNMP and WMI credentials, and produce a comprehensive visual network diagram during security assessments.

* **Core Steps:**

  * Launch SolarWinds Network Topology Mapper with administrative privileges and create a new network map project or discovery wizard.

  * Configure the network discovery scan by defining the target IP address ranges or subnets and providing SNMP (such as community strings like public and private) and WMI credentials.

  * Execute the scan to process discovery data, monitor node discovery, packet exchanges, and map generation progress.

  * Review, organize, and export the generated visual network diagram illustrating device interconnections, links, and subnet layouts for documentation and reconnaissance analysis.


---








