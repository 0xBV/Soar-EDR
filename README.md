## Soar-EDR
This project demonstrates an end-to-end security orchestration and automation workflow using LimaCharlie EDR and Tines SOAR to detect, notify, and optionally isolate endpoints upon detection of malicious activity

## 📌 Playbook Objective
Send a Slack message to the user containing information about detections generated from Lima Charlie (EDR).  Generates a user prompt generated from Tines (SOAR) for playbook orchestration to isolate the affected machine.

## 🛠️ Technologies & Tools
- LimaCharlie EDR – Detection source and host isolation

- Tines SOAR – Orchestration and Slack/email-driven response

- Slack API – User notification and approval workflow

- Email Notifications – Automated alert delivery

- (Optional: Python scripts or HTTP Request steps in Tines)
