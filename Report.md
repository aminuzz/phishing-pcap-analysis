# PHISHING / SMTP FORENSIC REPORT


---

## Summary
This investigation analyzed captured SMTP network traffic (.pcap files) to identify phishing or extortion activity.  
Malicious messages originated from **10.6.1.104**.  
Other messages contained Outlook `winmail.dat` files that decoded to harmless formatting icons.  
All analysis was performed inside an isolated virtual machine.

---

## Methodology
1. Opened PCAPs in **Wireshark**.  
2. Filtered for `smtp` and `smtp.data.fragments`.  
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
| **Kali Linux VM** | Safe analysis environment |
| **Base64 Decoder & SHA256** | Extract and hash attachments |

---

## Findings and Analysis

### PCAP A – Outlook TNEF Attachment
Wireshark view of SMTP traffic showing the encoded `winmail.dat` message:
<img width="1910" height="889" alt="image" src="https://github.com/user-attachments/assets/6f24259b-eb53-41b8-9e0c-ad9c34f3d447" />



Thunderbird rendering of the same message with the visible `winmail.dat` attachment:
<img width="1910" height="920" alt="image" src="https://github.com/user-attachments/assets/e23a6420-9fc5-4e31-ac9d-587678ec48d9" />


Decoded `winmail.dat` revealed only an Outlook formatting icon:
<img width="1909" height="884" alt="image" src="https://github.com/user-attachments/assets/2420afbb-64b7-421f-ada0-96f3eae4fbbf" />



**Result:** No malicious payload; benign RTF formatting data.

---

### PCAP B – No Significant Activity
No executable or suspicious attachments identified.  
<img width="1915" height="883" alt="image" src="https://github.com/user-attachments/assets/08afe9ed-c927-46e3-aa5e-a74d7afa4317" />


---

### PCAP C – Primary Malicious Actor
SMTP traffic from **10.6.1.104** contained multiple extortion-style messages:
<img width="1909" height="885" alt="image" src="https://github.com/user-attachments/assets/0db53a97-0a3b-45ba-beac-227d1079127d" />

Thunderbird view of one of the phishing/extortion emails:
<img width="1908" height="878" alt="image" src="https://github.com/user-attachments/assets/07df2c8c-bba1-46f2-b331-0ceb165b2996" />


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
| **Base64 Strings** | Z2FsdW50 / VjF2MXRyMG4= | Possibly credentials |

---

## Recommendations and Next Steps
- Preserve PCAPs and extracted files with SHA256 hashes.  
- Block or monitor traffic to/from `10.6.1.104`.  
- Keep all decoding inside isolated environments.  


---

## Conclusion
The analysis identified **10.6.1.104** as the malicious source of phishing/extortion traffic.  
Other Outlook `winmail.dat` attachments were verified as non-malicious.  
This project demonstrates practical email-forensics workflow and documentation.

---

