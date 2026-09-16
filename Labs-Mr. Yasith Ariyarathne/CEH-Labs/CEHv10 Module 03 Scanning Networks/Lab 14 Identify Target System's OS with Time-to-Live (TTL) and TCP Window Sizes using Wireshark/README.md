# Lab 14: Identify Target System's OS with Time-to-Live (TTL) and TCP Window Sizes using Wireshark

## 1. Laboratory Overview & Objectives

The objective of this lab is to demonstrate how to identify the operating system of a target system by inspecting the Time-to-Live (TTL) and TCP window size fields in the IP and TCP headers using Wireshark during ethical hacking and penetration testing operations.

* **Target System / Environment:** Windows Server 2016 / Windows 10 / Ubuntu VM
* **Primary Tools:** Wireshark

---

## 2. Step-by-Step Task Execution & Evidence

### Task 1: Launch Wireshark and Start Packet Capture

1. Launched Wireshark with administrative privileges on the host system.
2. Selected the active network interface (e.g., Ethernet or Wi-Fi) and started the packet capture.

📸 **Verification Screenshot 1: Launching Wireshark and Starting Capture**
![Launching Wireshark and Starting Capture](./screenshots/lab14_task1_launch_wireshark.jpg)

### Task 2: Generate Network Traffic to Target System

1. Initiated a connection (such as an ICMP ping or a TCP connection via port scanning/netcat/browser) to a target machine (Windows 10, Windows Server 2016, or Ubuntu VM).
2. Filtered the captured packets in Wireshark (using filters like `ip.addr == <target_ip>` or `tcp`) to isolate the traffic originating from the target system.

📸 **Verification Screenshot 2: Filtering Target Traffic**
![Filtering Target Traffic](./screenshots/lab14_task2_filter_traffic.jpg)

### Task 3: Inspect IP Header TTL and TCP Window Size

1. Clicked on the initial packet in the TCP handshake (SYN-ACK or SYN packet) from the target machine.
2. Expanded the Internet Protocol section in the packet details pane to inspect the Time to Live (TTL) value.
3. Expanded the Transmission Control Protocol section to examine the Window size value (or Window size).

📸 **Verification Screenshot 3: Inspecting TTL and TCP Window Size**
![Inspecting TTL and TCP Window Size](./screenshots/lab14_task3_inspect_headers.jpg)

### Task 4: Correlate TTL and Window Size with Target Operating System

1. Analyzed the captured values against known OS fingerprinting databases:
   * **Windows:** Initial TTL typically 128, TCP Window Size often multiples of 8192 (e.g., 8192, 64240, 65535).
   * **Linux/Unix:** Initial TTL typically 64, TCP Window Size often 5840, 5720, or 65535.
2. Confirmed the operating system of the target machine based on these header characteristics.

📸 **Verification Screenshot 4A: Linux OS Identification (TTL 64)**
![Linux OS Identification Result](./screenshots/lab14_task4_verify_os_linux.jpg)

📸 **Verification Screenshot 4B: Windows OS Identification (TTL 128)**
![Windows OS Identification Result](./screenshots/lab14_task4_verify_os_windows.jpg)

---

## 3. Lab Questions & Technical Analysis

**Question 1: Why are the Initial Time-to-Live (TTL) and TCP Window Size values reliable indicators for OS fingerprinting?**

* **Answer:** Different operating system vendors implement network stack parameters differently. The default initial TTL (e.g., 64 for Linux, 128 for Windows) and default TCP window sizes are hardcoded or configured per OS architecture, allowing security analysts to deduce the remote OS even when services are hidden or firewalled.

**Question 2: How can intermediate routers affect the TTL value observed in Wireshark, and how do analysts account for it?**

* **Answer:** Each router hop along the network path decrements the packet's TTL value by 1 before forwarding it. Analysts account for this by looking at the initial hop limit—rounding up the received TTL to the nearest standard baseline (e.g., a received TTL of 53 implies an initial TTL of 64 with 11 hops along the path).

---

## 4. Laboratory Reflection

This lab provided practical experience in passive operating system fingerprinting using Wireshark. By capturing network traffic, isolating TCP handshake packets, and analyzing IP header TTLs alongside TCP window sizes, we successfully identified remote operating systems without actively intrusive scanning. Mastering network header analysis is essential for reconnaissance, vulnerability mapping, and accurate asset identification during security assessments.