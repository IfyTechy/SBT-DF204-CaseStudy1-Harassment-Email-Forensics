# SBT-DF204 Case Study 1: Investigating Harassment Email Traffic With Wireshark

A formal digital forensics packet analysis investigating a simulated harassment email complaint sent via the anonymous web messaging service `willselfdestruct.com`. Prepared for **SBT-DF204 (Computer Forensics Case Studies)**, this investigation covers PCAP evidence acquisition, SHA-256 integrity verification, HTTP payload extraction, Layer 2/3 endpoint identification, session cookie correlation, and attribution analysis under open wireless network conditions.

---

## 📌 Investigation Overview

- **Lead Examiner:** Nebeuwa Ifeanyichukwu Raphael
- **Course & Module:** SBT-DF204 - Computer Forensics Case Studies (Case Study 1)
- **Target Scenario:** Harassment email traffic analysis (Nitroba University Scenario)
- **Primary Tools:** `Wireshark`, `tshark`, `sha256sum`
- **Evidence Dataset:** `nitroba.pcap` (Source: Digital Corpora)

### Key Forensic Findings
- **Evidence Integrity:** Verified original PCAP download integrity and created a working copy with strict SHA-256 hash tracking.
- **Web Service Traffic:** Isolated client HTTP interactions with `www.willselfdestruct.com` using targeted Wireshark display filters.
- **Message Payload Correlation:** Extracted HTTP POST parameters and form data matching the reported self-destructing harassment email.
- **Device Identification:** Mapped Layer 3 client IP addresses to Layer 2 source MAC addresses to track host behavior across shared DHCP pools.
- **Identity & Roster Attribution:** Analyzed HTTP session cookies and browser traffic to link the physical device to a student profile, evaluating its presence against the Chemistry 109 class roster.
- **Attribution Limits:** Documented evidentiary limitations, noting that IP/MAC address presence on an open, unencrypted wireless router does not guarantee suspect identity without supporting host-level artifacts.

---

## 📁 Repository Structure

```text
SBT-DF204-CaseStudy1-Harassment-Email-Forensics/
├── evidence/
│   └── nitroba.pcap                    # Original captured network evidence file
├── working/
│   └── nitroba_working.pcap            # Working copy used during packet analysis
├── reports/
│   ├── evidence_hashes.txt             # SHA-256 checksum logs for raw & working evidence
│   ├── http_requests.txt              # Exported TShark HTTP GET/POST logs
│   ├── tcp_streams.txt                 # Reconstructed TCP streams for web sessions
│   ├── endpoint_mac_mapping.tsv        # MAC to IP address mapping table
│   └── cookie_artifacts.txt            # Extracted session cookies & identity indicators
├── screenshots/                        # Numbered evidence screenshots with active filters
├── SBTDF204_CaseStudy1_Report.pdf      # Final submitted digital forensics PDF report
└── README.md
```

## 📝 Evidence Log Template

| Evidence ID | Packet / Item | Finding | Why It Matters | Screenshot / Appendix |
| :--- | :--- | :--- | :--- | :--- |
| **E01** | `nitroba.pcap` | Downloaded PCAP file SHA-256 hash calculated prior to opening | Establishes chain of custody and proves evidence integrity | Appendix A - Hash Log |
| **E02** | Packet #`<NUM>` | HTTP GET request to `www.willselfdestruct.com` | Identifies client initiation of communication with target web service | Appendix B - Web Request |
| **E03** | Packet #`<NUM>` | HTTP POST request with form payload data | Contains submitted message metadata and form parameters correlating to harassment email | Appendix C - POST Payload |
| **E04** | Frame #`<NUM>` | Ethernet source MAC address `<MAC_ADDR>` mapped to IP `<CLIENT_IP>` | Pinpoints physical network interface card (NIC) on the local subnet | Appendix D - MAC Mapping |
| **E05** | Packet #`<NUM>` | HTTP Cookie header containing email address string `<EMAIL>` | Binds physical device session to a specific user account identity | Appendix E - Cookie Header |
| **E06** | Roster Match | Identity linked to `<STUDENT_NAME>` verified against Chem 109 roster | Evaluates whether identified host user is enrolled in Chemistry 109 | Appendix F - Roster Verification |

---
