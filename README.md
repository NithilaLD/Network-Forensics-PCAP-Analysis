# Network Forensics & PCAP Analysis – Incident Investigation

A network forensic investigation of a simulated cyber-harassment incident involving the analysis of a network packet capture (`XYZ.pcap`). The project demonstrates the use of network forensic techniques to trace suspicious activity, correlate network identifiers, reconstruct an activity timeline, and identify the device and user associated with the malicious activity.

## 📌 Project Overview

The investigation was conducted as part of an academic network forensics and incident response scenario.

The objective was to analyse captured network traffic from a university dormitory network and determine which individual was responsible for sending harassing emails to a Chemistry 109 instructor.

The investigation involved:

* Mapping the network infrastructure
* Identifying relevant network devices
* Tracing suspicious network traffic
* Locating TCP flows associated with the hostile messages
* Correlating IP addresses with MAC addresses
* Identifying browser and operating-system information
* Analysing DNS and HTTP traffic
* Investigating email authentication activity
* Reconstructing the attacker's activity timeline
* Preserving and documenting supporting evidence

## 🔍 Investigation Workflow

```text
XYZ.pcap
   │
   ▼
Network Traffic Examination
   │
   ▼
Identify Network Devices
   │
   ▼
Trace Suspicious IP Address
   │
   ▼
Correlate IP ↔ MAC Address
   │
   ▼
Analyse TCP / HTTP / DNS Traffic
   │
   ▼
Identify Email & Browser Evidence
   │
   ▼
Reconstruct Activity Timeline
   │
   ▼
Correlate Evidence
   │
   ▼
Final Forensic Finding
```

## 🛠️ Tools Used

| Tool              | Purpose                                                                         |
| ----------------- | ------------------------------------------------------------------------------- |
| Wireshark         | Packet capture analysis, filtering, TCP stream analysis and protocol inspection |
| NetworkMiner      | Host discovery, network traffic analysis and extraction of relevant information |
| Kali Linux        | Forensic analysis environment                                                   |
| Windows 11        | Secondary analysis and cross-verification environment                           |
| Hash Verification | Evidence integrity verification                                                 |

The analysis used Wireshark and NetworkMiner to examine the captured network traffic and cross-check relevant findings.

## 📊 PCAP Details

| Property           | Value                         |
| ------------------ | ----------------------------- |
| Capture File       | `XYZ.pcap`                    |
| Format             | PCAP                          |
| Total Packets      | 94,410                        |
| Capture Size       | Approximately 56 MB           |
| Capture Duration   | 4 hours 22 minutes 39 seconds |
| Primary Analysis   | Wireshark                     |
| Cross-Verification | NetworkMiner                  |

## 🧪 Methodology

The investigation followed a structured network forensic process.

### 1. PCAP Integrity Verification

MD5, SHA1 and SHA256 hashes were calculated and verified before analysis to support evidence integrity.

### 2. Network Identification

Network endpoints, IP addresses and MAC addresses were examined to identify the important devices involved in the captured traffic.

### 3. Suspicious Device Identification

The investigation isolated the private IP address:

```text
192.168.15.4
```

and correlated it with the MAC address:

```text
00:17:f2:e2:c0:ce
```

The device was identified as an Apple Macintosh system.

### 4. Traffic Filtering

Wireshark display filters were used to narrow the investigation to relevant traffic, including:

```text
ip.addr == 192.168.15.4
```

```text
eth.addr == 00:17:f2:e2:c0:ce
```

```text
ip.addr == 192.168.15.4 && http
```

```text
http.host contains "willselfdestruct"
```

```text
frame contains "lily"
```

```text
http.cookie_pair
```

### 5. TCP & HTTP Analysis

Relevant TCP streams and HTTP requests were examined to identify communication associated with the harassment activity.

### 6. Email Correlation

Email authentication and cookie evidence were analysed to associate the suspicious device with the `jcoachj` email account.

### 7. Timeline Reconstruction

Network activity was reconstructed to identify searches, website visits and communications occurring before and during the harassment activity.

### 8. Evidence Correlation

Multiple independent indicators were correlated rather than relying on a single packet or identifier.

## 🕵️ Key Findings

The investigation identified `192.168.15.4` as the primary suspicious internal IP address.

The device was associated with:

```text
MAC Address: 00:17:f2:e2:c0:ce
Device: Apple Macintosh
IP Address: 192.168.15.4
```

Relevant traffic included searches relating to harassment, anonymous email services and communications associated with the reported threats.

Important packet references included:

| Packet | Finding                                                          |
| -----: | ---------------------------------------------------------------- |
|  74920 | Search relating to the legal consequences of harassing a teacher |
|  78967 | Email login activity associated with `jcoachj`                   |
|  79715 | Cleartext Gmail cookie associated with `jcoachj`                 |
|  80614 | Activity involving `sendanonymousmail.net`                       |
|  83601 | Activity involving `willselfdestruct.com`                        |

The report ultimately correlated these findings with the Chemistry 109 class list and identified Johnny Coach as the perpetrator within the simulated scenario.

## 📁 Evidence

The [`Evidence`](https://github.com/NithilaLD/Network-Forensics-PCAP-Analysis/tree/main/Evidence) directory contains the supporting forensic artefacts referenced throughout the report.

### Evidence Files

| ID   | Description                                |
| ---- | ------------------------------------------ |
| EV1  | Private IP proof                           |
| EV2  | WillSelfDestruct packet capture            |
| EV3  | WillSelfDestruct DNS information           |
| EV4  | Specific MAC address evidence              |
| EV5  | Threat messages sent to Lily               |
| EV6  | Searches performed by the MAC address      |
| EV7  | Packet 74920 incriminating evidence        |
| EV8  | Email logins within the network            |
| EV9  | Elishevet-related information              |
| EV10 | Mail logons from the MAC address           |
| EV11 | JCoach email evidence from the MAC address |
| EV12 | JCoach cookie pairs                        |
| EV13 | JCoach comparison with MAC address         |
| EV14 | TCP stream proofing                        |

## 📄 Project Report

The complete forensic investigation is documented in:

[`Project Report.pdf`](https://github.com/NithilaLD/Network-Forensics-PCAP-Analysis/blob/main/Project%20Report.pdf)

The report includes:

* Executive Summary
* Network Capture Details
* Network Components
* Methodology
* Detailed Findings
* Network Structure
* Activity Timeline
* Background Evidence
* Supporting Evidence
* Conclusions
* Appendix
* Self-Review

## 🎯 Learning Outcomes

This project provided practical experience in:

* Network packet analysis
* PCAP investigation
* Wireshark filtering
* TCP stream reconstruction
* HTTP and DNS analysis
* IP/MAC correlation
* NetworkMiner investigation
* Digital evidence handling
* Cryptographic hash verification
* Incident response methodology
* Forensic documentation
* Evidence-based investigation

## 👥 Team

This was completed as a group investigation.

**Members:**

* [Dulan Nithila Liyanarachchi](https://github.com/NithilaLD)
* [Dulsara Nipunanga](https://github.com/Nibbles0)

The report documents individual contributions in the self-review section.

## ⚠️ Disclaimer

This project was completed for academic and educational purposes using a simulated network forensic scenario and provided packet-capture data.

The findings should not be interpreted as evidence concerning real individuals or real-world incidents.

## 📚 References

The complete methodology, evidence references, packet analysis and conclusions are available in the project report.

---
