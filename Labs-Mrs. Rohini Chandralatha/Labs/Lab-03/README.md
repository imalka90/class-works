# Lab Practice: Task 3 - TCP/IP Stack Tweaking

## 1. Task Overview & Objectives

The objective of this task is to harden the Windows TCP/IP network stack via the system registry to mitigate potential Denial of Service (DoS) and Distributed Denial of Service (DDoS) vectors, specifically TCP SYN flood attacks. By customizing key connection parameters, the operating system reduces memory consumption during unacknowledged TCP handshakes and speeds up session cleanup.

* **Target OS:** Windows Laboratory Host
* **Management Tool:** Registry Editor (`regedit.exe`)
* **Key Registry Hive:** `HKLM\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`

---

## 2. Step-by-Step Task Execution & Evidence

### Task 3: TCP/IP Stack Tweaking

1. Opened the Registry Editor (`regedit`) and navigated to the network stack path: `HKLM\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`.
2. Created/updated the DWORD value `SynAttackProtect` and set it to `1` or `2` to enable proactive SYN flood defense mechanisms.
3. Configured `EnablePMTUDiscovery` to `0` to prevent attackers from exploiting Path MTU discovery mechanisms to force connection fragmentation or bandwidth exhaustion.
4. Adjusted `KeepAliveTime` to a lower millisecond/second threshold to drop inactive connections faster and preserve system resources.

> **📸 Verification Screenshot 3: TCP/IP Stack DoS Mitigation Parameters**
> ![TCP/IP Stack Tweaking](./screenshots/task3_stack_tweaking.png)

---

## 3. Technical Analysis & Lab Questions

**Question: How does setting `SynAttackProtect` help defend a host against TCP SYN flood attacks?**

* **Answer:** During a TCP SYN flood attack, an attacker exhausts host memory resources by flooding the system with connection requests without completing the three-way handshake. Enabling `SynAttackProtect` causes the OS to defer memory allocation for half-open connections, reduces retry timeouts for unacknowledged SYN-ACK packets, and forces early connection teardowns, keeping the host responsive.


