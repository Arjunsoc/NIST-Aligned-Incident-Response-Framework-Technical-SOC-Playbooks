# SOC Playbook: Credential Compromise

## 1. Scenario Overview
This playbook governs the technical response to the suspected or confirmed compromise of user identity credentials, specifically targeting Azure AD (Microsoft 365) and Okta SSO accounts within the AgriLogix environment.

## 2. PICERL Execution Steps

### Step 1: Preparation (Pre-Incident)
*   Ensure Azure AD 'Impossible Travel' and 'Anomalous Location' alerts are actively forwarding to Splunk.
*   Verify that Okta MFA is strictly enforced for all remote fleet operators and corporate staff.
*   Maintain an updated resolver list for the Infrastructure Identity Team.

### Step 2: Identification (Detection & Analysis)
The L1/L2 SOC Analyst must investigate the alert to confirm a true positive compromise.
*   **Log Verification:** Review Splunk for multiple failed login attempts followed by a successful login.
*   **Geolocation Check:** Cross-reference the source IP address of the successful login against the employee's known physical location. 
*   **Behavioral Analysis:** Check Azure AD audit logs for immediate, suspicious actions post-login (e.g., creating new Inbox rules, exporting SharePoint documents, or modifying MFA factors).

### Step 3: Containment
Once validated by the Incident Commander, immediate action must be taken to sever the attacker's access.
*   **Account Suspension:** Suspend the compromised user account directly in the Okta administration portal.
*   **Token Revocation:** Execute a "Revoke all active sessions/tokens" command within Azure AD to immediately terminate any active Microsoft 365 connections.
*   **Network Isolation:** If the credentials were used to establish a VPN or remote Prisma Access session, manually terminate the active tunnel.

### Step 4: Eradication
Remove the attacker's foothold and any artifacts left behind.
*   **Password Reset:** Force a strict, out-of-band password reset for the affected user.
*   **MFA Audit:** Strip any unverified or newly added Multi-Factor Authentication devices from the user's Okta profile.
*   **Rule Purge:** Delete any malicious email forwarding or inbox manipulation rules created by the threat actor in Exchange Online.

### Step 5: Recovery
Restore the user's access securely.
*   **Re-enablement:** Unsuspend the Okta account and walk the employee through the secure password reset process via phone or secure IT channel.
*   **Enhanced Monitoring:** Place the recovered account on a 72-hour watchlist within Splunk, configuring Wazuh to alert on any high-risk commands executed by that user.

### Step 6: Lessons Learned
*   Conduct a brief review to determine how the credential was compromised (e.g., credential stuffing, phishing, or infostealer malware on a personal device).
*   Adjust Conditional Access policies in Azure AD to permanently block the attacker's IP subnet or ASN.
