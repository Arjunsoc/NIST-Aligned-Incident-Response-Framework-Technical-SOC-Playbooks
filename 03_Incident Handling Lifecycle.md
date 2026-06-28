# NIST Incident Handling Lifecycle Policy

## 1. Overview and Methodology
This document outlines the overarching Incident Response (IR) strategy for AgriLogix Cold Chain Solutions. The framework governing this enterprise policy is based on the **NIST SP 800-61 Rev. 2** Computer Security Incident Handling Guide. 

While this four-phase NIST lifecycle dictates the high-level operational and management strategy, the granular, step-by-step tactical execution used by Security Operations Center (SOC) analysts during an active threat is governed by the six-step **SANS PICERL** methodology, detailed in the attached Incident Specific Playbooks.

## 2. The Four Phases of Incident Response

### Phase 1: Preparation
Preparation involves the continuous hardening of the AgriLogix infrastructure and the readiness of the Cyber Security Incident Response Team (CSIRT).
*   **Infrastructure Hardening:** Continuous maintenance of the Zero Trust architecture, including the regular auditing of Azure AD Conditional Access policies and Okta Single Sign-On (SSO) integrations.
*   **Vulnerability Management:** Routine proactive scanning of the AWS infrastructure and cold-storage OT networks using Nmap, and application testing via Burp Suite.
*   **Detection Engineering:** Tuning Wazuh (XDR) and Splunk (SIEM) detection rules to reduce alert fatigue and ensure high-fidelity alerting for SOC analysts.
*   **Training:** Conducting bi-annual tabletop exercises for the CSIRT and maintaining updated out-of-hours escalation contact lists.

### Phase 2: Detection and Analysis
The objective of this phase is to rapidly identify anomalous activity, validate whether the alert constitutes a true security incident, and determine the initial scope.
*   **Alert Triage:** L1/L2 SOC analysts monitor Splunk dashboards for correlated telemetry from Palo Alto Prisma firewalls, AWS CloudTrail, and endpoint logs.
*   **Validation:** Analysts determine if the event is a false positive (benign) or a true positive. True positives are immediately escalated to the Incident Commander.
*   **Initial Scoping:** Establishing the "blast radius" of the incident. This includes identifying compromised user credentials, affected IP addresses, and determining if the threat has laterally moved into the isolated warehouse OT networks.

### Phase 3: Containment, Eradication, and Recovery
NIST groups these tactical responses into a single phase focused on stopping the threat and restoring business operations.
*   **Containment:** Halting the attacker's progression. Actions may include utilizing Wazuh active response to isolate an endpoint from the network, revoking compromised Okta access tokens, or implementing emergency block rules on the Palo Alto firewalls.
*   **Eradication:** Removing the threat artifacts from the environment. This includes deleting malicious payloads, rebuilding infected Windows workstations, and disabling malicious inbox rules in Microsoft 365.
*   **Recovery:** Carefully restoring operations to a known good state. This involves restoring logistics databases from clean AWS backups, forcing enterprise-wide password resets, and monitoring the network closely for reignition of the attack.

### Phase 4: Post-Incident Activity (Lessons Learned)
After the threat is neutralized and normal operations resume, the CSIRT must conduct a retrospective review to improve future defenses.
*   **Root Cause Analysis:** Determining exactly how the attacker breached the environment (e.g., a missed patch, a successful phishing email, or a misconfigured AWS S3 bucket).
*   **Documentation:** Finalizing the incident timeline, calculating the financial or operational impact, and ensuring all legal and compliance obligations regarding data exposure have been met.
*   **Continuous Improvement:** Updating the specific SOC Playbooks and Splunk detection rules based on the new threat intelligence gathered during the incident to prevent a recurrence.
