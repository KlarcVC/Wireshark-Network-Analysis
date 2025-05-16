# Wireshark Traffic Analysis – Qakbot Malware Detection

This project is a deep-dive traffic analysis of a PCAP file that simulates a real-world malware infection scenario. Using Wireshark and public tutorials, I analyzed network traffic to identify infected clients, understand attack behavior, and extract the malware sample.

## 🔍 Exercise Overview

**Source:** [Malware Traffic Analysis - 2020-04-24](https://www.malware-traffic-analysis.net/2020/04/24/index.html)  
**Network Range:** `10.0.0.0/24`  
**Domain:** `steelcoffee.net`  
**Goal:**  
- Identify Windows clients and user accounts  
- Detect infected machine  
- Analyze and confirm malware type  

## 🧠 Key Findings

- **Windows Clients Identified:**
  - `10.0.0.149` - `DESKTOP-C10SKPY` - `alyssa.fitzgerald`
  - `10.0.0.167` - `DESKTOP-GRIONXA` - `elmer.obrien`

- **Infected Host:** `10.0.0.167`
- **Malware:** Qakbot (Qbot)
- **Infection Indicator:** 
  - Suspicious HTTP response from `alphapioneer.com` disguised as an image but delivered a Windows executable.
  - Triggered alert: `ET MALWARE Windows executable sent when remote host claims to send an image`.

## 🔧 Tools Used

- Wireshark
- tcp.port filters & stream analysis
- HTTP object extraction
- SHA256 hashing
- [Any.Run](https://app.any.run/) sandbox for malware behavior confirmation
- Virustoal hash integrity check

## 📎 Resources

- [Using Wireshark - Identifying Hosts and Users](https://unit42.paloaltonetworks.com/using-wireshark-identifying-hosts-and-users/)
- [Using Wireshark - Display Filter Expressions](https://unit42.paloaltonetworks.com/using-wireshark-display-filter-expressions/)
- [Exporting Objects from a Pcap](https://unit42.paloaltonetworks.com/using-wireshark-exporting-objects-from-a-pcap/)

## 📂 File Structure

- `analysis-notes.pdf` – Summary of key findings
- `screenshots/` – Evidence of infected streams, object extraction
- `pcap/` – Original packet capture (not included due to size)

---

## 🚀 Try It Yourself

Clone the repo and load the PCAP file in Wireshark to follow the infection trail. Filter with:

```bash
tcp.port == 51132

