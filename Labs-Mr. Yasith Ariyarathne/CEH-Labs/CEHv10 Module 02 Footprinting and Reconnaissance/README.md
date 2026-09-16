# CEH Module 02 — Footprinting & Reconnaissance

This document covers detailed steps, command executions, and expected outputs for conducting open-source intelligence (OSINT) and reconnaissance across Windows and Kali Linux environments.

**Labs 1–9: Open Source Information Gathering & Reconnaissance**

---

## Table of Contents

1. [Lab 1 Open Source Information Gathering (Windows Command Line)](#lab-1-open-source-information-gathering-windows-command-line) — [View Lab](./Lab%2001%20Open%20Source%20Information%20Gathering%20(Windows%20Command%20Line)/)

2. [Lab 2 Finding Subdomains using Sublist3r (Kali Linux)](#lab-2-finding-subdomains-using-sublist3r-kali-linux) — [View Lab](./Lab%2002%20Finding%20Subdomains%20using%20Sublist3r%20(Kali%20Linux)/)

3. [Lab 3 Gathering Personal Information using Online People Search](#lab-3-gathering-personal-information-using-online-people-search) — [View Lab](./Lab%2003%20Gathering%20Personal%20Information%20using%20Online%20People%20Search/)

4. [Lab 4 Gathering Information from LinkedIn using InSpy (Kali Linux)](#lab-4-gathering-information-from-linkedin-using-inspy-kali-linux) — [View Lab](./Lab%2004%20Gathering%20Information%20from%20LinkedIn%20using%20InSpy%20(Kali%20Linux)/)

5. [Lab 5 Web Reconnaissance via Firebug Developer Tools](#lab-5-web-reconnaissance-via-firebug-developer-tools) — [View Lab](./Lab%205%20Web%20Reconnaissance%20via%20Firebug%20%20Developer%20Tools/)

6. [Lab 6 Extracting Data using Web Data Extractor](#lab-6-extracting-data-using-web-data-extractor) — [View Lab](./Lab%2006%20Extracting%20Data%20using%20Web%20Data%20Extractor/)

7. [Lab 7 Mirroring Website using HTTrack Web Site Copier](#lab-7-mirroring-website-using-httrack-web-site-copier) — [View Lab](./Lab%2007%20Mirroring%20Website%20using%20HTTrack%20Web%20Site%20Copier/)

8. [Lab 8 Tracing Emails using eMailTrackerPro](#lab-8-tracing-emails-using-emailtrackerpro) — [View Lab](./Lab%2008%20Tracing%20Emails%20using%20eMailTrackerPro/)

9. [Lab 9 Domain Information Lookup via SmartWhois](#lab-9-domain-information-lookup-via-smartwhois) — [View Lab](./Lab%2009%20Domain%20Information%20Lookup%20via%20SmartWhois/)

10. [Lab 10 Website Footprinting (Central Ops & OSINT Tools)](#lab-10-website-footprinting-central-ops--osint-tools) — [View Lab](./Lab%2010%20Website%20Footprinting%20(Central%20Ops%20&%20OSINT%20Tools)/)

---

## Lab 1 — Open Source Information Gathering (Windows Command Line)

### Tasks 1 & 2: Ping & Maximum Frame Size Identification

1. Open `cmd.exe` as Administrator.
2. Obtain the target IP address:

```dos
ping www.certifiedhacker.com
```

3. Determine maximum frame size (testing ICMP payload limits without fragmentation):

```dos
ping www.certifiedhacker.com -f -l 1500
ping www.certifiedhacker.com -f -l 1472
```

> **Verification:** Successful reply received at size 1472 without needing packet fragmentation.

---

### Task 3: TTL Expiration & Emulate Tracert

1. Observe TTL expiration in transit:

```dos
ping www.certifiedhacker.com -i 3
```

2. Map the complete route of hops to the target:

```dos
tracert www.certifiedhacker.com
```

> **Verification:** Terminal displays "TTL expired in transit" responses alongside the completed hop list from `tracert`.

---

### Tasks 4–7: DNS Queries via nslookup

1. Launch interactive mode:

```dos
nslookup
```

2. Query the A record (IP address):

```text
set type=a
www.certifiedhacker.com
```

3. Query the CNAME and primary name server:

```text
set type=cname
certifiedhacker.com
```

4. Resolve the name server IP:

```text
set type=a
ns1.bluehost.com
```

> **Verification:** Output resolves the target's IP records and primary authoritative name server details.

---

## Lab 2 — Finding Subdomains using Sublist3r (Kali Linux)

1. Update system packages and install Sublist3r:

```bash
sudo apt update && sudo apt -y install sublist3r
```

2. Execute subdomain enumeration via Bing:

```bash
sublist3r -d google.com -t 3 -e bing
```

3. Filter subdomains with open port 80:

```bash
sublist3r -d google.com -p 80 -e bing
```

> **Verification:** Output enumerates discovered subdomains, filtered specifically for active HTTP service on port 80.

---

## Lab 3 — Gathering Personal Information using Online People Search

> **Note:** Pipl (`https://pipl.com`) has transitioned to a restricted, paid enterprise model and is no longer available for free public OSINT. **Epieos** (`https://epieos.com`) was selected as a free alternative.

Epieos uses passive enumeration by querying public API endpoints and password recovery mechanisms of third-party platforms (e.g. Google, Trello, Duolingo) on the analyst's behalf — without authenticating or attempting to log into the target's account, so no security alerts or login notifications are triggered.

1. Navigate to [https://epieos.com](https://epieos.com) in a browser.
2. Execute a search for a target individual (e.g. a sample name or email from the lab's exercise sheet).
3. Inspect the aggregated public records, including associated history, usernames, and addresses.

> **Verification:** Browser displays an aggregated profile summary card for the target subject.

---

## Lab 4 — Gathering Information from LinkedIn using InSpy (Kali Linux)

1. Install InSpy on Kali Linux:

```bash
sudo apt update && sudo apt -y install inspy
```

2. Verify the default wordlist directory:

```bash
ls -ls /usr/share/inspy/wordlists/
```

3. Run Employee Spy (`empspy`) targeting an organisation:

```bash
inspy --empspy /usr/share/inspy/wordlists/title-list-large.txt google
```

> **Verification:** Terminal displays identified employee titles and associated profile records.

---

## Lab 5 — Web Reconnaissance via Firebug Developer Tools

1. Open Firefox on Kali Linux and load `http://www.moviescope.com`.
2. Press `F12` to launch Developer Tools (Firebug).
3. Inspect the **Console / Security** tab to identify unencrypted HTTP authentication flags.
4. Open the **Network (NET)** tab, click any GET request, and inspect the response headers.

> **Verification:** Response headers clearly disclose web server signatures (e.g. `Server: Microsoft-IIS`, `X-Powered-By: ASP.NET`).

---

## Lab 6 — Extracting Data using Web Data Extractor

1. Launch `wde.exe` (Web Data Extractor).
2. Click **New** and enter the starting URL: `http://www.certifiedhacker.com`.
3. Enable options for: **Meta tags**, **Emails**, **Phone numbers**, and **Body Text**.
4. Click **Start** and allow parsing to complete.

> **Verification:** Navigating to the Emails and Phones tabs displays collected contact metadata extracted from site pages.

---

## Lab 7 — Mirroring Website using HTTrack Web Site Copier

1. Open **WinHTTrack Website Copier**.
2. Create a project named `Test Project`.
3. Set the Target Web Address to `https://www.certifiedhacker.com`.
4. Configure scan rules and initiate the mirroring process.
5. Once completed, click **Browse Mirrored Website**.

> **Verification:** Web browser displays mirrored content with a local storage path in the address bar (e.g. `file:///C:/.../index.html`).

---

## Lab 8 — Tracing Emails using eMailTrackerPro

1. Open the targeted email message, select **Show Original**, and copy the full header text.
2. Launch **eMailTrackerPro**.
3. Navigate to **My Trace Reports > Trace Headers**.
4. Paste the raw internet headers into the input area and click **Trace**.

> **Verification:** Application renders hop details, an IP geolocation map, and originating ISP information.

---

## Lab 9 — Domain Information Lookup via SmartWhois

1. Launch **SmartWhois**.
2. Query domain names or target IP addresses obtained during prior reconnaissance phases.

> **Verification:** Application displays the domain registrant profile, contact entries, and authoritative DNS servers.

---

# Lab 10: Website Footprinting (Central Ops & OSINT Tools)

### Part 1: Initial Query Setup & Address Lookup

1. Opened the web browser inside Kali Linux and navigated to `https://centralops.net/co/`.
2. Entered the target domain `www.certifiedhacker.com` into the **Domain Dossier** search utility.
3. Enabled checkmarks for **domain whois record**, **network whois record**, and **DNS records**.
4. Executed the query to initiate passive reconnaissance.
5. Analyzed the returned **Address lookup** results:
   * **Canonical Name:** `certifiedhacker.com`
   * **Aliases:** `www.certifiedhacker.com`
   * **Addresses:** `162.241.216.11`

   > **Verification:** Central Ops Interface and Address Lookup,Domain WHOIS Record Analysis,Network WHOIS and IP Assignment Details,DNS Records and PTR Reverse Lookups.