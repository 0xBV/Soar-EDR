## ⚙️ SOAR-EDR Automation Project
This project demonstrates an end-to-end security orchestration and automation workflow using LimaCharlie (EDR) and Tines (SOAR) to detect, notify, and optionally isolate endpoints upon detection of malicious activity

## 📌 Playbook Objective
Send a Slack message to the user containing information about detections generated from LimaCharlie (EDR).  Generates a user prompt from Tines (SOAR) for playbook orchestration to optionally isolate the affected workstation.
Message to the user contains these fields:
- Time
- Hostname
- Source IP
- Process
- Command Line
- File Path
- Sensor ID
- Link to Detection (If applicable)

<img width="743" alt="image" src="https://github.com/user-attachments/assets/bb000908-e6aa-4bf5-a4c7-2d4d04b1b85e" />

## 🛠️ Technologies & Tools
- LimaCharlie EDR – Detection source and host isolation

- Tines SOAR – Orchestration and Slack/email-driven response

- Slack API – User notification and approval workflow

- Email Notifications – Automated alert delivery

