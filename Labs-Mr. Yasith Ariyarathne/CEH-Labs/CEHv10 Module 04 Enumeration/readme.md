# Module 04: Enumeration Labs

This repository contains practical laboratory documentation, procedure logs, and analysis covering **Module 04: Enumeration**. These labs demonstrate techniques used by security professionals to perform system and network enumeration, extracting critical target intelligence such as NetBIOS names, active user accounts, shared resources, system services, and software inventories across target networks.

---

# System & Network Enumeration Lab Series — Index

1. [Lab 1 NetBIOS Enumeration using Global Network Inventory](#lab-1-netbios-enumeration-using-global-network-inventory) — [View Lab](./Lab%201%20NetBIOS%20Enumeration%20using%20Global%20Network%20Inventory/)

2. [Lab 2 Enumerating Network Resources using Advanced IP Scanner](#lab-2-enumerating-network-resources-using-advanced-ip-scanner) — [View Lab](./Lab%202%20Enumerating%20Network%20Resources%20using%20Advanced%20IP%20Scanner/)

3. [Lab 3 Performing Network Enumeration using SuperScan](#lab-3-performing-network-enumeration-using-superscan) — [View Lab](./Lab%203%20Performing%20Network%20Enumeration%20using%20SuperScan/)

4. [Lab 4 Enumerating Resources in a Local Machine using Hyena](#lab-4-enumerating-resources-in-a-local-machine-using-hyena) — [View Lab](./Lab%204%20Enumerating%20Resources%20in%20a%20Local%20Machine%20using%20Hyena/)

5. [Lab 5 Performing Network Enumeration using NetBIOS Enumerator](#lab-5-performing-network-enumeration-using-netbios-enumerator) — [View Lab](./Lab%205%20Performing%20Network%20Enumeration%20using%20NetBIOS%20Enumerator/)

6. [Lab 6 Enumerating a Network using SoftPerfect Network Scanner](#lab-6-enumerating-a-network-using-softperfect-network-scanner) — [View Lab](./Lab%206%20Enumerating%20a%20Network%20using%20SoftPerfect%20Network%20Scanner/)

7. [Lab 7 Enumerating a Target Network using Nmap and Net Use](#lab-7-enumerating-a-target-network-using-nmap-and-net-use) — [View Lab](./Lab%207%20Enumerating%20a%20Target%20Network%20using%20Nmap%20and%20Net%20Use/)

8. [Lab 8 Enumerating Services on a Target Machine](#lab-8-enumerating-services-on-a-target-machine) — [View Lab](./Lab%208%20Enumerating%20Services%20on%20a%20Target%20Machine/)

9. [Lab 9 SNMP Enumeration using SNMP Enum](#lab-9-snmp-enumeration-using-snmp-enum) — [View Lab](./Lab%209%20SNMP%20Enumeration%20using%20SNMP%20Enum/)

10. [Lab 10 LDAP Enumeration using Active Directory Explorer](#lab-10-ldap-enumeration-using-active-directory-explorer) — [View Lab](./Lab%2010%20LDAP%20Enumeration%20using%20Active%20Directory%20Explorer/)

11. [Lab 11 Enumerating Information from Windows and Samba Host using Enum4linux](#lab-11-enumerating-information-from-windows-and-samba-host-using-enum4linux) — [View Lab](./Lab%2011%20Enumerating-Information-from-Windows-and-Samba-Host-using-Enum4linux/)

---

## Technical Overview & Environment Requirements

* **Primary Attacker Systems:** Kali Linux (Nmap, snmp_enum, enum4linux), Windows Server / Windows 10/11 (GUI enumeration tools)
* **Target Environment:** Multi-OS Network (Windows Server 2012/2016, Windows 10, Samba Hosts)
* **Core Toolsets:** Global Network Inventory, Advanced IP Scanner, SuperScan, Hyena, NetBIOS Enumerator, SoftPerfect Network Scanner, Nmap, Zenmap, nbtstat, `net use`, snmp_enum, ADExplorer, Enum4linux.

---

## Comprehensive Lab Index

### Lab 1: NetBIOS Enumeration using Global Network Inventory
* **Topic:** Agent-Free Network Reconnaissance and System Inventory
* **Objective:** Use Global Network Inventory (GNI) to perform agent-free network reconnaissance, extracting operating systems, BIOS info, NetBIOS names, user groups, services, and installed software across target IP ranges.
* **Core Steps:**
  * Launch Global Network Inventory with administrative privileges.
  * Configure the target network scan range and administrative/NetBIOS access credentials.
  * Execute the agent-free network scan across target IP subnets.
  * Review and export inventory data, examining NetBIOS names, workgroup/domain membership, and system services.

### Lab 2: Enumerating Network Resources using Advanced IP Scanner
* **Topic:** Subnet Scanning, Host Discovery, and Resource Share Auditing
* **Objective:** Use Advanced IP Scanner to rapidly discover live hosts on a subnet, inspect open shared folders, and evaluate network resource accessibility.
* **Core Steps:**
  * Define the target IP address range and initiate the fast multi-threaded network scan.
  * Inspect discovered live hosts, IP addresses, MAC addresses, and vendor metadata.
  * Expand host entries to view shared folders and execute remote management options.

### Lab 3: Performing Network Enumeration using SuperScan
* **Topic:** Windows Host Enumeration, NetBIOS Name Tables, and Null Sessions
* **Objective:** Use SuperScan 4.1 to perform comprehensive Windows host enumeration, querying NetBIOS name tables, null sessions, account policies, shares, and listening services.
* **Core Steps:**
  * Configure host and port lists within SuperScan for target reconnaissance.
  * Execute port scans and ping sweeps to verify active services.
  * Perform NetBIOS enumeration to extract domain details, user accounts, and shared resources.

### Lab 4: Enumerating Resources in a Local Machine using Hyena
* **Topic:** GUI-Based Local System Administration and Resource Enumeration
* **Objective:** Use Hyena to perform explorer-style deep management and enumeration of local users, running services, user rights, and scheduled jobs.
* **Core Steps:**
  * Launch Hyena and connect to the local machine or target system workspace.
  * Navigate system containers to examine user accounts, groups, and membership.
  * Audit running services, user rights assignments, and scheduled administrative tasks.

### Lab 5: Performing Network Enumeration using NetBIOS Enumerator
* **Topic:** NetBIOS Connection Probing and Workstation Analysis
* **Objective:** Use NetBIOS Enumerator to probe active NetBIOS connections across a target IP range to extract NetBIOS names, workstation types, and domain structures.
* **Core Steps:**
  * Input the target IP address range into NetBIOS Enumerator.
  * Initiate the enumeration sweep targeting NetBIOS session and name service ports.
  * Extract and analyze resolved NetBIOS names, service types, and connected workgroups.

### Lab 6: Enumerating a Network using SoftPerfect Network Scanner
* **Topic:** Multi-Threaded Host Discovery and Hidden Share Auditing
* **Objective:** Use SoftPerfect Network Scanner for multi-threaded scanning of live MAC addresses, hidden/writable shares, and checking custom or standard network ports.
* **Core Steps:**
  * Configure the IP address range and multi-threaded ping settings.
  * Run the scan to discover live hosts, MAC address vendors, and active operating systems.
  * Filter results for shared resources, writable folders, and open listening ports.

### Lab 7: Enumerating a Target Network using Nmap and Net Use
* **Topic:** NetBIOS Port Auditing, Remote Name Querying, and Share Mapping
* **Objective:** Use Nmap, Zenmap, `nbtstat`, and `net use` commands to identify open NetBIOS ports (135, 137–139, 445), query remote NetBIOS name tables, and test null session connectivity.
* **Core Steps:**
  * Run Nmap scans targeting NetBIOS and SMB ports on the target machine.
  * Use `nbtstat -A <Target IP>` to query remote NetBIOS name tables and MAC addresses.
  * Execute `net use \<Target IP>\IPC$ "" /user:""` to test unauthenticated null session access and enumerate shares.

### Lab 8: Enumerating Services on a Target Machine
* **Topic:** Service Version Detection, OS Fingerprinting, and TCP Port Sweeping
* **Objective:** Use Nmap on Kali Linux to perform ping sweeps, stealthy SYN scans (`-sS`), and service version/OS detection (`-sV -O`) to pinpoint exploitable software.
* **Core Steps:**
  * Execute host discovery ping sweeps across the target subnet.
  * Run a stealth SYN scan (`nmap -sS <Target IP>`) to identify open listening ports without completing the full TCP handshake.
  * Perform service version detection and OS fingerprinting (`nmap -sV -O <Target IP>`) to catalog software builds and kernel versions.

### Lab 9: SNMP Enumeration using SNMP Enum
* **Topic:** Simple Network Management Protocol Information Extraction
* **Objective:** Query Simple Network Management Protocol (SNMP) using `snmp_enum` to extract device information, routing tables, user accounts, and running services.
* **Core Steps:**
  * Identify target systems with UDP port 161 (SNMP) open.
  * Test default community strings (such as `public` and `private`).
  * Execute `snmp_enum` against the target to extract system configurations, interface lists, and software inventory.

### Lab 10: LDAP Enumeration using Active Directory Explorer
* **Topic:** Active Directory Database Inspection and Object Attribute Enumeration
* **Objective:** Use Active Directory Explorer (ADExplorer) to navigate and analyze Active Directory databases, object structures, and user/group attributes.
* **Core Steps:**
  * Launch ADExplorer and connect to the target domain controller or LDAP server.
  * Browse the hierarchical directory tree (DIT) to inspect organizational units (OUs), users, computers, and groups.
  * Examine object properties and security descriptors to identify misconfigurations or privilege pathways.

### Lab 11: Enumerating Information from Windows and Samba Host using Enum4linux
* **Topic:** Comprehensive Linux-Based Windows/Samba Host Enumeration
* **Objective:** Use Enum4linux on Kali Linux to extract target information from Windows and Samba hosts, including user accounts, shares, password policies, and OS details.
* **Core Steps:**
  * Verify network reachability and SMB/NetBIOS port availability on the target host.
  * Execute `enum4linux -a <Target IP>` to perform a comprehensive automated enumeration sweep.
  * Review extracted output detailing user lists, share mappings, group memberships, and password complexity policies.

---
