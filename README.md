## ⚙️ Soar-EDR Project
This project demonstrates an end-to-end security orchestration and automation workflow using LimaCharlie (EDR) and Tines (SOAR) to detect, notify, and optionally isolate endpoints upon detection of malicious activity

## 📌 Playbook Objective
Send a Slack message to the user containing information about detections generated from LimaCharlie (EDR).  Generates a user prompt generated from Tines (SOAR) for playbook orchestration to optionally isolate the affected workstation.

<img width="775" alt="image" src="https://github.com/user-attachments/assets/6d200bf6-a757-4cb6-833d-9e9ebbb54d09" />


## 🛠️ Technologies & Tools
- LimaCharlie EDR – Detection source and host isolation

- Tines SOAR – Orchestration and Slack/email-driven response

- Slack API – User notification and approval workflow

- Email Notifications – Automated alert delivery

