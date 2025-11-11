# 🕵️‍♂️ phishing-pcap-analysis  
📧 **Network Forensics & Phishing Detection using Wireshark**

---

## 📘 Overview  
This project demonstrates the process of analyzing captured network traffic (**.pcap files**) to detect and investigate phishing attacks and Windows malware.  
By inspecting **SMTP and email traffic** in Wireshark, I identified **malicious IP addresses**, examined **phishing email headers and subject lines**, and extracted indicators of compromise (IOCs) to understand the full attack chain.  

💡This analysis was performed in a **secure virtual environment** to ensure safe handling of potentially malicious data.

---

## 🧩 Objectives  
- Inspect `.pcap` files to identify phishing and malware activity  
- Analyze **SMTP traffic** and extract suspicious email details  
- Identify and document **malicious IP addresses**  
- Examine **email subject lines** and message headers for phishing patterns  
- Trace the **origin and flow** of the phishing attack  
- Strengthen skills in **Wireshark, traffic analysis, and network forensics**

---

## ⚙️ Tools & Technologies  

| Tool / Service | Purpose |
|-----------------|----------|
| **Wireshark** | Capture and analyze network packets |
| **SMTP Filters** | Isolate email traffic for phishing detection |
| **.pcap Files** | Network traffic data for forensic analysis |
| **.eml Files** | Email message data for header/content inspection |
| **Virtual Machine Environment** | Safe, isolated workspace for malware-related analysis |

---

## 🧱 Methodology  

### 1️⃣ Load and Inspect .pcap Files  
Opened captured traffic files in Wireshark to observe all packets and protocols.  

### 2️⃣ Apply SMTP Filters  
Used filters such as `smtp` and `smtp.data.fragments` to narrow focus on email exchanges.  

### 3️⃣ Identify Suspicious IP Addresses  
Traced network flows and identified IP addresses associated with malicious senders or external hosts.  

### 4️⃣ Analyze Email Content  
Reviewed subject lines and message headers in `.eml` files to identify phishing lures and social engineering tactics.  

### 5️⃣ Trace the Attack Origin  
Mapped connections between client and external IPs to determine how phishing emails entered the network.  

---

## 📸 Screenshots & Findings  
Screenshots in this repository show:  
- Extracted **phishing email traffic** from `.pcap` files  
- Identification of **malicious IP addresses**  
- Inspection of **email subject lines** and **SMTP conversations**  

> ⚠️ **Note:** The original `.pcap` and `.eml` files are excluded to prevent misuse.  
> You can apply the same techniques described here on safe sample datasets to replicate the analysis.  

---

## 📂 Repository Contents  

| File / Folder | Description |
|----------------|--------------|
| `README.md` | Project overview and documentation |
| `Report.md` | Detailed findings, methodology, and conclusions |

---

## ⚠️ Important Cybersecurity Note  
This project involves handling network captures that may contain malware or malicious payloads.  
Always perform `.pcap` analysis inside a **virtualized and isolated environment**.  
Use tools like **Wireshark** or **tcpdump** for analysis only — never open attachments or execute extracted files.

---

## 🧾 Outcome  
✅ Successfully analyzed phishing-related network traffic using Wireshark.  
✅ Identified malicious IPs, email subject patterns, and attack origin.  
✅ Strengthened practical understanding of **cybersecurity forensics** and **network analysis techniques**.  

---

## 🚀 Future Enhancements  
- Automate IOC extraction using Python or Scapy  
- Integrate with SIEM tools (e.g., Splunk) for alert correlation  
- Expand analysis to include HTTP/HTTPS phishing detection  
- Develop a dashboard to visualize attack flow and IOCs  

---

## 🧩 Skills Demonstrated  
- Network traffic analysis with Wireshark  
- Email header and SMTP investigation  
- Malware/phishing forensics  
- IP tracing and indicator correlation  
- Secure analysis environment configuration  

---


