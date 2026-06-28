# Company Profile: Arjun'S Cold Chain Solutions

## 1. Organization Overview
* **Company Name:** Arjun's Cold Chain Solutions
* **Industry:** Logistics, Agricultural Cold Storage, and Supply Chain Management
* **Headquarters:** Alathur, Kerala (Primary Fulfillment & Cold Storage Hub)
* **Business Model:** B2B agricultural logistics, providing temperature-controlled warehousing and fleet routing for perishable goods across the Palakkad-Thrissur transit corridor.
* **Compliance & Risk:** As a vital link in the regional food supply chain, AgriLogix is subject to strict data protection regulations regarding vendor contracts, employee data, and automated facility operational technologies (OT).

## 2. Infrastructure & Network Architecture
AgriLogix operates a hybrid-cloud infrastructure heavily leaning toward a Zero Trust Security Framework to protect both physical supply chain operations and corporate data.

* **Endpoints:** 450+ managed workstations (Windows 11) distributed across corporate offices and warehouse fulfillment centers.
* **Cloud Infrastructure:** Core logistics databases and supply chain routing applications are hosted on AWS.
* **Corporate IT:** Microsoft 365 is utilized for all corporate communications, document management (SharePoint), and email exchange.
* **Operational Technology (OT):** IoT temperature sensors and automated cold-storage cooling units are segmented on a dedicated physical network at the fulfillment centers.

## 3. Enterprise Security Stack
The Security Operations Center (SOC) utilizes a consolidated security stack to monitor telemetry across the hybrid environment. These tools form the basis of the actions detailed in the Incident Response Playbooks.

* **SIEM / Log Aggregation:** Splunk (Primary alert dashboard) and Wazuh (HIDS/XDR telemetry from endpoints).
* **Identity & Access Management (IAM):** Azure AD (for Microsoft 365 ecosystem) integrated with Okta for seamless SSO across third-party logistics SaaS platforms.
* **Network & Cloud Security:** Palo Alto Prisma (securing the AWS environment and managing secure edge access for remote fleet operators).
* **Vulnerability Management:** Regular internal scanning and VAPT conducted utilizing Burp Suite (web apps) and Nmap (network discovery).
