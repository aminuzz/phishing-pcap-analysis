# PHISHING / SMTP FORENSIC REPORT
**By Aminuz Zaman**  
**November 2025**

---

## Executive Summary
This investigation analyzed captured SMTP network traffic (.pcap files) to identify phishing or extortion activity.  
Malicious messages originated from **10.6.1.104**.  
Other messages contained Outlook `winmail.dat` files that decoded to harmless formatting icons.  
All analysis was performed inside an isolated virtual machine.

---

## Methodology
1. Opened PCAPs in **Wireshark**.  
2. Filtered for `smtp` and `smtp.data`.  
3. Followed TCP streams to reconstruct full emails.  
4. Inspected MIME parts for `Content-Type`, filenames, and base64 sections.  
5. Extracted and decoded `winmail.dat` attachments using **tnef** inside a VM.

---

## Tools Used
| Tool | Purpose |
|------|----------|
| **Wireshark** | Capture and analysis of SMTP traffic |
| **Thunderbird** | Visual reconstruction of messages |
| **TNEF Viewer / tnef** | Decode Outlook `winmail.dat` attachments |
| **Linux VM** | Safe analysis environment |
| **Base64 Decoder & SHA256** | Extract and hash attachments |

---

## Findings and Analysis

### PCAP A – Outlook TNEF Attachment
Wireshark view of SMTP traffic showing the encoded `winmail.dat` message:
![SMTP traffic](Screenshots/Screenshot_2025-11-11_151036.png)

Thunderbird rendering of the same message with the visible `winmail.dat` attachment:
![Thunderbird message](Screenshots/Screenshot_2025-11-11_145546.png)

Decoded `winmail.dat` revealed only an Outlook formatting icon:
![Extracted icon](Screenshots/Screenshot_2025-11-11_153330.png)

**Result:** No malicious payload; benign RTF formatting data.

---

### PCAP B – No Significant Activity
No executable or suspicious attachments identified.  
![SMTP DATA fragments](Screenshots/Screenshot_2025-11-11_150831.png)

---

### PCAP C – Primary Malicious Actor
SMTP traffic from **10.6.1.104** contained multiple extortion-style messages:
![Malicious IP traffic](Screenshots/Screenshot_2025-11-11_155416.png)

Thunderbird view of one of the phishing/extortion emails:
![Extortion email](Screenshots/Screenshot_2025-11-11_151551.png)

**Assessment:** Confirmed malicious source; phishing/extortion campaign traced to `10.6.1.104`.

---

### PCAP D – Duplicate of A
Similar `winmail.dat` formatting artifacts; no malware detected.

---

## Indicators of Compromise (IOCs)
| Type | Value | Notes |
|------|-------|-------|
| **Malicious IP** | 10.6.1.104 | Origin of extortion messages |
| **Benign Artifact** | winmail.dat → info-16.png | Outlook formatting icon |
| **Base64 Strings** | Z2FsdW50 / VjF2MXRyMG4= | Possibly credentials – redact for public repo |

---

## Recommendations and Next Steps
- Preserve PCAPs and extracted files with SHA256 hashes.  
- Block or monitor traffic to/from `10.6.1.104`.  
- Keep all decoding inside isolated environments.  
- When publishing to GitHub, omit PCAPs and redact any PII.

---

## Conclusion
The analysis identified **10.6.1.104** as the malicious source of phishing/extortion traffic.  
Other Outlook `winmail.dat` attachments were verified as non-malicious.  
This project demonstrates practical email-forensics workflow and documentation.

---

*© 2025 Aminuz Zaman — Phishing / SMTP Forensic Report*
