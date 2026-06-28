# Incident Severity and Escalation Matrix

To ensure a rapid and proportional response, AgriLogix Cold Chain Solutions categorizes security incidents into four severity levels. The severity dictates the maximum allowable response time and the required escalation path.

## Severity Classification

| Severity | Definition & Business Impact | Examples in AgriLogix Environment | Target Response Time |
| :--- | :--- | :--- | :--- |
| **Low** | Isolated event with no significant impact on business operations or data confidentiality. Typically contained automatically by security tools. | - Blocked phishing email.<br>- Malware quarantined by Wazuh on a single corporate laptop.<br>- Failed brute-force login attempts. | **Within 24 Hours** (Next Business Day) |
| **Medium** | Localized incident requiring manual intervention to contain. Potential risk to a single system or user account, but core logistics operations remain unaffected. | - Successful phishing click (no creds entered).<br>- Active malware on a single endpoint requiring isolation.<br>- Anomalous Azure AD sign-in from an untrusted location. | **Within 4 Hours** (During Business Hours) |
| **High** | Severe incident causing localized outages or data exposure. Lateral movement detected, or disruption to a specific fulfillment center's operations. | - Compromise of an active Okta SSO session.<br>- IoT temperature sensors in a warehouse pushed offline.<br>- Unauthorized access to AWS S3 buckets containing vendor data. | **Within 1 Hour** (24/7/365 Escalation) |
| **Critical** | Catastrophic event threatening the survival of the business. Complete shutdown of the supply chain routing system, widespread encryption, or massive data exfiltration. | - Ransomware deployment across the AWS logistics database.<br>- Complete takeover of the Microsoft 365 global admin account.<br>- Coordinated DDoS attack halting the Palakkad-Thrissur fleet routing. | **Immediate** (24/7/365 All-Hands) |

## Escalation Path & Out-of-Hours Contacts

When a High or Critical severity incident is validated by Tier 1/Tier 2 analysts, the following escalation chain must be triggered immediately, regardless of the time of day:

1. **Primary Escalation:** Incident Commander (SOC Lead) via PagerDuty / On-Call Mobile.
2. **Secondary Escalation (If Commander Unreachable):** Director of Infrastructure.
3. **Resolver Group Activation:** The Incident Commander initiates an emergency bridge call (via a secure out-of-band communication channel like Signal) and pages the on-call Infrastructure/Network Engineers.
4. **Executive Notification:** For Critical incidents, the Incident Commander notifies the Legal Liaison and C-Suite within 2 hours of incident confirmation.
