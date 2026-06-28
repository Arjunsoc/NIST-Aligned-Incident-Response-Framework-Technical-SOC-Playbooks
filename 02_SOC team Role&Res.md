# Cyber Security Incident Response Team (CSIRT) Roles & Responsibilities

During a security incident at AgriLogix Cold Chain Solutions, a structured chain of command is critical for rapid containment and clear communication. The following roles define the responsibilities of the CSIRT members.

## Core CSIRT (Direct Response)

*   **L1 / L2 SOC Analysts (Triage & Validation):** Responsible for continuously monitoring the Splunk and Wazuh dashboards. Their primary duty is to validate whether an alert is a true positive, gather initial telemetry (e.g., source IP, affected endpoints), and escalate confirmed incidents to the Incident Commander.
*   **Incident Commander (SOC Lead):** The central authority during an active incident. This role is responsible for declaring an official incident, coordinating all technical response efforts, approving containment actions (such as isolating a host or disabling an Okta account), and maintaining the official incident timeline.
*   **Threat Hunter / Subject Matter Expert (SME):** Engaged for complex incidents (e.g., ransomware or advanced persistent threats). Responsible for deep forensic analysis, reverse-engineering malicious payloads, and providing advanced eradication strategies.

## Extended CSIRT (Resolvers & Support)

*   **Infrastructure & Network Engineering:** The technical resolver group responsible for executing physical or network-level changes requested by the Incident Commander, such as modifying Palo Alto Prisma firewall rules, restoring AWS cloud backups, or physically disconnecting OT hardware in the fulfillment centers.
*   **Legal & Compliance Liaison:** Responsible for advising the CSIRT on regulatory obligations regarding data breaches, managing evidence chain-of-custody, and ensuring that any containment actions do not violate vendor contracts.
*   **Public Relations & Communications:** The sole entity authorized to draft internal employee communications and external press releases regarding system outages or data compromises.
*   **Executive Leadership (C-Suite):** Engaged only during High or Critical severity incidents. Responsible for making critical business decisions, such as authorizing the shutdown of core logistics operations or approving external incident response retainer engagements.
