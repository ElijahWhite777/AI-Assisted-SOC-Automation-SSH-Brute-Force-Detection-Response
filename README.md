# AI-Assisted-SOC-Automation-SSH-Brute-Force-Detection-Response

📌 Project Overview

This project demonstrates a **Tier-2 SOC–level automated detection, enrichment, and response pipeline** designed to identify and respond to **SSH brute-force attacks** using a modern **SIEM + SOAR + AI-assisted analysis** workflow.

The system simulates how a real Security Operations Center (SOC) operates by:
- Detecting suspicious authentication behavior in a SIEM
- Automating alert handling through a SOAR platform
- Enriching Indicators of Compromise (IOCs) with threat intelligence
- Performing Tier-2 SOC analysis using AI
- Delivering a structured incident report to Slack for analyst action

This is not a basic lab — it models **real SOC detection, triage, enrichment, and response practices**.

---

## 🧠 Skills Demonstrated

- SIEM Detection Engineering (Splunk)
- SOC Alert Triage & Investigation
- SOAR Automation (n8n)
- Threat Intelligence & IOC Enrichment (AbuseIPDB)
- MITRE ATT&CK Mapping
- NIST Incident Response Framework
- AI-Assisted Tier-2 SOC Analysis
- Security Reporting & Communication
- Automation & Workflow Engineering

---

## 🏗️ Architecture Overview

**End-to-End Flow**
Windows Authentication Logs
↓
Splunk SIEM
↓
SSH Brute-Force Detection Rule
↓
Webhook Alert Trigger
↓
n8n SOAR Workflow
↓
IOC Enrichment (AbuseIPDB)
↓
AI Tier-2 SOC Analysis
↓
Slack Incident Report

📸 **Architecture Diagram**


---

## 🔍 Detection Logic – Splunk SIEM

### Detection Use Case
The Splunk detection rule identifies **multiple failed SSH login attempts** originating from a single external IP within a defined time window — a common indicator of brute-force attacks.

### Detection Indicators
- Repeated failed authentication attempts
- Common brute-force usernames (root, admin, oracle, postgres, etc.)
- Single external IP targeting repeated login attempts
- SSH service (TCP/22)

📸 **Splunk Detection Rule**
<img width="798" height="890" alt="splunk detection rule" src="https://github.com/user-attachments/assets/0c223aec-b112-4b5b-8fc5-1b0a6056f6ee" />

📸 **splunk query**
<img width="1244" height="985" alt="Splunk search query" src="https://github.com/user-attachments/assets/96904ddb-a059-48fc-8b90-cf9477095603" />


---

## ⚙️ SOAR Automation – n8n Workflow

The SOAR workflow automates the following actions:

1. Receives Splunk alerts via webhook
2. Evaluates alert thresholds (failed login count)
3. Enriches source IP with AbuseIPDB threat intelligence
4. Sends enriched data to an AI model
5. Generates a Tier-2 SOC incident report
6. Delivers the report to Slack

📸 **n8n Workflow Canvas**

<img width="1286" height="1003" alt="n8n workflow canvas" src="https://github.com/user-attachments/assets/6533fa7d-12f6-4712-ab1b-792bd7cf15e3" />

<img width="1288" height="1006" alt="webhook payload injestion" src="https://github.com/user-attachments/assets/7a4231fa-e109-4b23-b238-ed1856975115" />

---

## 🌐 IOC Enrichment – AbuseIPDB

The workflow enriches the detected source IP with:

- Abuse confidence score
- Total abuse reports
- Abuse categories
- Hosting provider
- Country of origin
- Historical attack activity

This enrichment validates malicious intent and strengthens confidence in attack classification.

📸 **AbuseIPDB Enrichment**

<img width="1294" height="1003" alt="abuse ipdb ioc enrichment threat intel" src="https://github.com/user-attachments/assets/3432e707-f8fb-4660-89aa-7467f1a21004" />

---

## 🤖 AI Tier-2 SOC Analysis

An AI model is configured to operate as a **Tier-2 SOC Analyst**, performing:

- Incident summarization
- Attack classification
- MITRE ATT&CK mapping
- NIST Incident Response alignment
- Risk justification
- Containment and escalation recommendations

The AI is restricted to **professional SOC output** — no generic or conversational responses.

📸 **AI Prompt Configuration**

<img width="1283" height="1003" alt="Ai prompt configuration tier 2 Analyst role" src="https://github.com/user-attachments/assets/36b38dd9-3f89-40de-8268-bf57bf35dd35" />

<img width="1918" height="1008" alt="Ai soc output analysis" src="https://github.com/user-attachments/assets/d66ea2eb-0d6f-49b9-8149-9ec89aeb211a" />

---

## 📘 MITRE ATT&CK Mapping

**Tactics Identified**
- Initial Access (TA0001)
- Reconnaissance (TA0043)

**Techniques Identified**
- Brute Force (T1110)
- Credential Guessing (T1110.001)

📸 **MITRE ATT&CK Mapping Output**

<img width="1920" height="1008" alt="NIST MITRE Slack top report" src="https://github.com/user-attachments/assets/31325358-a01a-4e69-9c97-1ca4ee7f4f6d" />


---

## 🧭 NIST Incident Response Alignment

This incident aligns with the following **NIST IR phases**:

- **Detection & Analysis** – SIEM alerting and IOC enrichment
- **Containment** – Blocking malicious IP and limiting SSH exposure
- **Eradication** – Credential hardening and brute-force prevention
- **Recovery** – Monitoring for residual activity
- **Post-Incident Activity** – Documentation and intelligence sharing

<img width="1920" height="1008" alt="NIST MITRE Slack top report" src="https://github.com/user-attachments/assets/6a676984-fac9-4746-b757-8ae8988fb0ed" />

---

## 📣 Slack Incident Report Output

The final output is a **Tier-2 SOC Incident Report** delivered automatically to Slack, containing:

- IOC summary
- Attack classification
- MITRE ATT&CK mapping
- NIST IR phases
- Risk assessment
- SOC response recommendations
- Escalation criteria
- Analyst confidence level

📸 **Slack Report (Top)**
<img width="1920" height="1008" alt="NIST MITRE Slack top report" src="https://github.com/user-attachments/assets/31395e7f-af79-4dad-88a5-1cc164a0944c" />


📸 **Slack Report (Bottom)**

<img width="1920" height="1006" alt="bottom slack report" src="https://github.com/user-attachments/assets/9b303726-4100-46b0-9c5b-ff53c6fa7e1f" />

---

## 🚨 Example SOC Recommendations Generated

- Block malicious IP at firewall / IDS / IPS
- Review SSH logs for successful authentication
- Enforce MFA and account lockout policies
- Implement rate-limiting or Fail2Ban
- Monitor for lateral movement
- Escalate if authentication succeeds or expands

---

## 🎯 Why This Project Matters

This project demonstrates:
- Real SOC detection engineering
- Automated security response workflows
- Threat-informed investigation
- Professional Tier-2 SOC reporting
- Practical application of MITRE & NIST frameworks

It reflects how **modern SOC teams actually operate**, not just theoretical lab exercises.

---

## 🚀 Future Enhancements

- Automated firewall blocking simulation
- Severity scoring (Low / Medium / High)
- Case management integration
- Multi-IOC correlation
- Security dashboard visualization

---

## 🧠 Final Notes

This project was built to mirror **real-world SOC workflows** and Tier-2 analyst responsibilities, combining detection engineering, automation, enrichment, and professional security reporting.



