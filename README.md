
​You​
# 🕵️ Passive Reconnaissance Project (OSINT Case Study)

### Author: **Bernard Mbata**
**Date:** October 21, 2025
**Role:** Cybersecurity Analyst
**Objective:** Demonstrate passive intelligence gathering techniques for mapping an organization’s attack surface using only **Open-Source Intelligence (OSINT)**.

---

## 🧠 Executive Summary
This project identifies publicly accessible data for a simulated target organization — **MegaCorp One** — using **passive reconnaissance** methods only.
Key discoveries included:
- Publicly available directories and archived contact lists
- Exposed subdomains and DNS infrastructure
- Metadata leakage from GitHub repositories

These findings illustrate how adversaries can profile an organization without directly interacting with its systems.

---

## ⚙️ Methodology

**Tools & Data Sources**
- Amass (passive mode)
- Whois lookups
- Wayback Machine
- Google Dorking / Directory Browsing
- Manual OSINT verification

**Rules of Engagement**
> Only publicly available information was collected — no active scanning or exploitation was performed.

---

## 🔍 Key Findings

### **Finding A — Whois Domain Enumeration**
- **Registrar:** Gandi SAS
- **Name Servers:** ns1, ns2, ns3.megacorpone.com
- **Domain Created:** 2013-01-22
- **Expiry:** 2024-01-22
These details help identify DNS infrastructure that could support phishing or DNS-based reconnaissance.

---

### **Finding B — GitHub JSON Metadata Exposure**
Metadata from GitHub’s API revealed:
- Repository URLs, owner details, and commit timestamps
- Indicators of active projects possibly exposing credentials
- Repository popularity (stars, forks, watchers) that help prioritize targets

---

### **Finding C — Archived Contact Information**
- The Wayback Machine exposed historical **emails and names of executives** still publicly available.
- `joe@megacorpone.com`
- `mcarlow@megacorpone.com`
- `alan@megacorpone.com`
**Risk:** High — enables phishing and impersonation.
**Recommendation:** Replace direct emails with a contact form and request archive removal.

---

### **Finding D — Directory Index Exposure**
- Public folders `/assets/img/team/` and `/assets/js/` listed internal resources.
**Risk:** Medium — reveals file structure and potential staff details.
**Recommendation:** Disable directory listing and audit access permissions.

---

### **Finding E — DNS Enumeration**
- Command used:
```bash
amass enum -passive -d megacorpone -o amass-passive.txt
