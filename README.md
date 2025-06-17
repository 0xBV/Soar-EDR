## ⚙️ SOAR-EDR Automation Project
This project demonstrates an end-to-end security orchestration and automation workflow using LimaCharlie (EDR) and Tines (SOAR) to detect, notify, and optionally isolate endpoints upon detection of malicious activity

## Playbook Objective
Send a Slack message to the user containing information about detections generated from LimaCharlie (EDR).  Generates a user prompt from Tines (SOAR) for playbook orchestration to optionally isolate the affected workstation.
Message to the user contain these fields:
- Time
- Hostname
- Source IP
- Process
- Command Line
- File Path
- Sensor ID
- Link to Detection (If applicable)

<img width="743" alt="image" src="https://github.com/user-attachments/assets/bb000908-e6aa-4bf5-a4c7-2d4d04b1b85e" />

## Technologies & Tools
- LimaCharlie EDR – Detection source and host isolation

- Tines SOAR – Orchestration and Slack/email-driven response

- Slack API – User notification and approval workflow

- Email Notifications – Automated alert delivery

## Generating telemetry for Detection Rule creation
I generated an event in LimaCharlie by triggering the execution of the "LaZagne.exe" program.  This program can be used maliciously for recovering stored passwords on a system post-exploitation.
MITRE ATT&CK Information:
- ID: S0349
- Type: TOOL
- Techniques Used: T1555, T1003, T1552

<img width="563" alt="image" src="https://github.com/user-attachments/assets/67054b96-d783-440f-b1e7-be8195d26b75" />

## Detection and Response rule creation
I generated a detection and response rule using the information from the manually generated event.  The rule I created makes sure that the event detected is a new or existing process on the Windows platform, with an OR rule to check if one of the parameters is true for file hash, file path, and the command line.
The primary response for this rule is to generate an alert under the "Detections" category of LimaCharlie.  The response rule also includes MITRE ATT&CK technique information.

<img width="554" alt="Detection Rule creation" src="https://github.com/user-attachments/assets/f8ec44a6-4fae-462d-b016-2f393a389a4b" />
<img width="353" alt="response_rule" src="https://github.com/user-attachments/assets/37ce0371-8d7d-4a91-b239-6eae8b1b30fe" />

## Tines (SOAR) 
Once the detection rule was generated and tested to work, I set up an output to a webhook I setup in Tines.  
The webhook is used to retrieve the detection and then have three separate actions:
- Send a message via Slack
<img width="523" alt="image" src="https://github.com/user-attachments/assets/9005294b-29ae-426c-a92f-66bf551f2837" />

- Send an email to the security analyst
<img width="341" alt="Detection_Email" src="https://github.com/user-attachments/assets/a634ce8e-7cf1-4234-9413-c4b9a9bf77cb" />

- Prompt the user with a detection alert, with a (yes/no) option to isolate the affected workstation
<img width="395" alt="User_Prompt" src="https://github.com/user-attachments/assets/b5784551-afe1-4009-ac29-206b55336708" />

Triggering the "Yes" condition will send a HTTP POST request to LimaCharlie to isolate the affected workstation.  Triggering the "No" condition will send a message via Slack, informing the user that the workstation was not isolated and to investigate.

## Summary 
<img width="1063" alt="image" src="https://github.com/user-attachments/assets/8a88b814-b28e-4b72-aba8-771979b017d8" />

