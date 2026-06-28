# SOC Playbook: Phishing & Malicious Email

## 1. Scenario Overview
This playbook dictates the response procedures for reported or detected phishing campaigns, spear-phishing attempts, and the delivery of malicious payloads via email within the AgriLogix Microsoft 365 environment.

## 2. PICERL Execution Steps

### Step 1: Preparation (Pre-Incident)
*   Ensure the "Report Phishing" button is deployed to all AgriLogix Outlook clients.
*   Maintain active anti-spam and Safe Links/Safe Attachments policies in Microsoft Defender for Office 365.
*   Ensure Wazuh agents are actively monitoring process creation on endpoints in case a payload is executed.

### Step 2: Identification (Detection & Analysis)
Analysts must determine the intent of the email and whether any user interacted with it.
*   **Header Analysis:** Extract the `.msg` or `.eml` file and analyze the email headers (using tools like MXToolbox) to identify the true sender IP, Return-Path, and any SPF/DKIM/DMARC failures.
*   **Artifact Detonation:** Submit any suspicious URLs or attachments to a secure sandbox (e.g., Any.Run or Hybrid Analysis) to observe behavior without risking the corporate network.
*   **Interaction Scoping:** Query Microsoft 365 unified audit logs and Splunk proxy logs to determine if the recipient (or any other employee) clicked the link, entered credentials, or downloaded the attachment.

### Step 3: Containment
Prevent further exposure or lateral movement if the user interacted with the threat.
*   **Email Quarantine:** Utilize Microsoft 365 Security/Exchange Admin Center to perform a soft-delete or quarantine of the malicious email across all enterprise inboxes.
*   **Network Blocking:** Add the malicious sender domain, IP address, and URLs to the Palo Alto Prisma blocklist.
*   **Endpoint Isolation:** If the user downloaded and executed a payload, immediately use the Wazuh active response capability to isolate the affected endpoint from the AgriLogix network.

### Step 4: Eradication
Remove the threat entirely from the environment.
*   **Hard Purge:** Execute a permanent purge (hard delete) of the malicious emails from the Microsoft 365 tenant.
*   **Malware Removal:** If a host was compromised, coordinate with Infrastructure to either run a deep offline antivirus scan or re-image the Windows workstation entirely.
*   **Account Reset:** If credentials were typed into a phishing portal, immediately trigger the **Credential Compromise Playbook** (force password reset, revoke tokens).

### Step 5: Recovery
Restore normal operations safely.
*   **Endpoint Reconnection:** Once verified clean (or re-imaged), remove the Wazuh isolation status and reconnect the workstation to the domain.
*   **User Notification:** Inform the employee who reported the email that the threat has been neutralized, reinforcing positive security behavior.

### Step 6: Lessons Learned
*   Review why the email bypassed initial Microsoft 365 spam filters and adjust mail flow rules accordingly.
*   If multiple users fell for the simulation/attack, recommend targeted security awareness training for that specific department.
