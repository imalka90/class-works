# Lab 3: Gathering Personal Information using Reverse Email Lookup (Epieos)

## 1. Laboratory Overview & Objectives

The objective of this lab is to perform Open Source Intelligence (OSINT) gathering on a target entity. **Note on Tool Selection:** The legacy tool Pipl (`https://pipl.com`) is no longer freely available and requires a paid enterprise subscription. To complete passive reconnaissance without paid enterprise access, this lab utilizes **Epieos** (`https://epieos.com`), a free OSINT reverse lookup engine. This technique allows security analysts to perform passive reconnaissance using an email address to uncover linked online profiles, connected web services (e.g., Google, Flickr, Trello), unique User IDs, and digital footprints for social engineering risk assessments.

* **Host System:** Windows 11 / Kali Linux
* **Reconnaissance Tool:** Epieos OSINT Tool (`https://epieos.com`) *(Selected replacement for Pipl)*
* **Target Query:** `dilanimalka@yahoo.com`

---

## 2. Step-by-Step Task Execution & Evidence

### Part 1: Navigating to the Alternative OSINT Utility

1. Opened the web browser inside Kali Linux.
2. Due to Pipl requiring a paid subscription, navigated to the free alternative reverse lookup engine: `https://epieos.com`.

### Part 2: Executing Reverse Email Lookup & Account Enumeration

1. Entered the target email address (`dilanimalka@yahoo.com`) into the primary lookup input field.
2. Executed the search query to identify linked Google accounts, profile photo availability, and connected web services.
3. Analyzed the returned profile aggregation results, taking note of associated Google account IDs, linked external platforms (e.g., Google Maps reviews, Flickr, Trello), and digital footprints across online services.

> **📸 Verification Screenshot 5: Web Browser Showing Aggregated Profile Data on Epieos**
> ![Web Browser Showing Aggregated Profile Data on Epieos](./screenshots/epieos_search.png)

---

## 3. Lab Questions & Technical Analysis

**Question 1: Why was Epieos selected over Pipl, and how do tools like Epieos discover linked services without alerting the target?**

* **Answer:** Pipl has transitioned to a restricted, paid enterprise business model, making it unavailable for free public OSINT analysis. Epieos was selected as a free alternative that uses passive enumeration methods by interacting directly with public API endpoints and password recovery mechanisms of third-party platforms (like Google, Trello, or Duolingo). Because it queries these public services on the analyst's behalf without authenticating or attempting to log into the victim's account, no security alerts or login notifications are triggered for the target user.

**Question 2: What are the primary cybersecurity risks associated with publicly discoverable email linkages across multiple services?**

* **Answer:** Exposing email linkages across multiple services allows attackers to map a target's digital ecosystem. Attackers can leverage unique account IDs and linked platforms to craft hyper-targeted spear-phishing attacks, conduct credential stuffing across discovered services, or reset account passwords using leaked OSINT data.

---

## 4. Laboratory Reflection

The lab successfully demonstrated passive OSINT reconnaissance using an email address via Epieos after pivoting from the paid Pipl tool. Aggregating profile data across platforms provides essential visibility into an individual's attack surface, highlighting how single data points like email addresses can reveal broader digital footprints across the web.