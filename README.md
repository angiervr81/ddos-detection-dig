# ddos-detection-dig
# 📘 CYB102 Capstone – Intrusion Detection & DDoS Analysis

**Team Name**: `BotnetBusters102`  
**Course**: CYB102 – Blue Team Fundamentals  
**Milestone**: 1 – *The Data Dig*  
**Dataset**: [CIC-IDS2017 – Intrusion Detection Evaluation Dataset](https://www.unb.ca/cic/datasets/ids-2017.html)  
**Playbook Used**: [GSPBC-1080 - Impact - Network Denial of Service](https://github.com/guardsight/gsvsoc_cirt-playbook-battle-cards/blob/master/GSPBC-1080%20-%20Impact%20-%20Network%20Denial%20of%20Service.pdf)

---

## 👥 Team Members

| Name               | Pronouns | Favorite Thing          |
|--------------------|----------|-------------------------|
| Dennys Antunish    | He/Him   | 🦈 Sharks              |
| Evgeniia Yeroshkina| She/Her  | 🍦 Vanilla              |
| Angie Rivera       | She/Her  | 🎡 McCarren Park       |
| Aliya Jones        | She/Her  | 🎮 Fortnite            |
| Navruz Asatullaev  | He/Him   | ☕ Water               |

---

## 🧠 Project Overview

This capstone project investigates a simulated **DDoS attack** using real-world data from the **CIC-IDS2017 dataset**. We use **Splunk**, **VirusTotal**, **AbuseIPDB**, and a professional SOC playbook to analyze, triage, and respond to the incident following industry-standard blue-team practices.

---

## 📂 Dataset Overview

- **Name**: CIC-IDS2017  
- **Source**: Canadian Institute for Cybersecurity (UNB)  
- **Format**: CSV & PCAP  
- **Scenarios**: DDoS, infiltration, botnet activity, brute force  
- **Focus File**: `Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv`

---

## 📌 Hypotheses

1. Multiple victims may appear in logs from July 7, 2017.
2. We expect high volumes of logs indicating a DDoS attempt.
3. The same source IP is used for repeated attacks.

---

## 🛠️ Tools Used

| Tool        | Purpose                                      |
|-------------|----------------------------------------------|
| Splunk      | Query and analyze network flow logs          |
| VirusTotal  | Threat intel and IP reputation checks        |
| AbuseIPDB   | Malicious IP lookup and reputation scoring   |
| Catalyst    | Case logging and incident documentation      |

---

## 🧾 Playbook Summary

- **Playbook**: `GSPBC-1080 – Network Denial of Service (DoS)`  
- **Creator**: GuardSight, USA  
- **Model**: PICERL (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned)  
- **Usage**: Aligned CSV flow data with playbook’s DDoS detection and mitigation phases.

---

## 🔍 Key Aspects

### 🔹 Monitoring Sources
Used Splunk queries on the CSV dataset to detect DDoS behavior, such as:

```spl
index=main source="Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv" Label="DDoS"
| stats count by "Source IP", "Destination IP", "Destination Port"

cyb102-ddos-analysis/
├── data/
│   └── Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv
├── queries/
│   └── splunk_ddos_queries.txt
├── reports/
│   └── milestone_summary.md
├── presentation/
│   └── slides.pptx
├── screenshots/
│   └── splunk_dashboard.png
│   └── catalyst_log.png
└── README.md

