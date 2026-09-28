<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/identity/standard-identity-security-management -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 6: Threat management and Defender Cloud Security

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

Identity access management is a critical component of cybersecurity in educational institutions. This article provides an overview of features and best practices for the A3 educational license. It covers essential tools and strategies to help IT administrators manage identities, secure access, and protect sensitive data in a school environment.

## Requirements

- Microsoft 365 A3 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Microsoft Advanced Threat Analytics

Microsoft Advanced Threat Analytics \(ATA\) is an on-premises platform designed to help protect your organization from advanced targeted cyber attacks and insider threats. While ATA is generally used in enterprise environments, it can also be highly beneficial in educational settings to safeguard sensitive information and ensure the security of your network.

**Key features of ATA:**

- **Behavioral analytics:** ATA uses behavioral analytics to learn the normal behavior of users and other entities in your organization. It then detects anomalies that could indicate potential threats.
- **Detection of advanced threats:** ATA can detect various types of advanced threats, including pass-the-ticket, pass-the-hash, and brute force attacks. It also identifies suspicious activities such as lateral movement and reconnaissance.
- **Clear incident reports:** The ATA console provides detailed reports on detected threats, including information on who was involved, what happened, when it occurred, and how the attack was carried out.
- **Integration with existing infrastructure:** ATA integrates with your existing network infrastructure, collecting data from domain controllers, DNS servers, and other sources to provide comprehensive security monitoring.

**Benefits for educational institutions:**

- **Protect sensitive data:** Safeguard student records, research data, and other sensitive information from cyber threats.
- **Enhance network security:** Monitor and detect suspicious activities within your network to prevent breaches.
- **Compliance:** Help meet regulatory requirements for data protection and security in educational environments.

**Getting started with ATA:**

1. Install ATA by deploying ATA Center and ATA Gateways in your network. The ATA Center processes data and generates alerts, while the Gateways capture and analyze network traffic.
2. Configure data sources by setting up port mirroring on your network devices to send traffic to the ATA Gateways. Alternatively, deploy ATA Lightweight Gateways directly on your domain controllers.
3. Monitor and respond by using the ATA console to monitor alerts and investigate suspicious activities. Take appropriate actions to mitigate identified threats.

**Learn more:**

- [What is Advanced Threat Analytics?](https://learn.microsoft.com/en-us/advanced-threat-analytics/what-is-ata)
- [Advanced Threat Analytics documentation](https://learn.microsoft.com/en-us/advanced-threat-analytics/)

## Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps is a powerful tool that can significantly enhance cybersecurity in educational environments. It helps protect your school's data and applications by providing comprehensive security for Software as a Service \(SaaS\) applications. Here are some key features and benefits:

- **Shadow IT discovery** identifies and monitors all cloud apps used within your institution, even those not officially sanctioned.
- **Threat protection** offers advanced threat detection and response capabilities to safeguard against cyber threats.
- **Information protection** ensures data security and compliance with various regulations.
- **SaaS security posture management** helps improve the security posture of your SaaS applications.

**Learn more:**

- [Microsoft Defender for Cloud Apps overview](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps)

## Microsoft Defender for Cloud App Discovery

Microsoft Defender for Cloud App Discovery is a feature within Microsoft Defender for Cloud Apps that helps you gain visibility into the cloud apps being used in your organization. This is useful for identifying and managing Shadow IT, ensuring that only approved and secure applications are in use.

**Key features:**

- **Cloud App Catalog** analyzes your traffic logs against a catalog of over 31,000 cloud apps. These apps are ranked and scored based on more than 90 risk factors.
- **Visibility and risk assessment** provides ongoing visibility into cloud app usage and assesses the risk posed by these apps. This helps in identifying potentially risky applications and taking appropriate actions.
- **Integration with existing tools** like Microsoft Defender for Endpoint to extend cloud discovery capabilities beyond your corporate network. It also supports integration with Secure Web Gateways \(SWGs\) and other security tools.
- **Automated and manual log upload** supports both manual and automated log uploads for continuous monitoring. You can use log collectors or APIs to automate the process.
- **Custom policies and anomaly detection** allows you to create custom policies to monitor and control cloud app usage. It also uses machine learning to detect anomalies in app usage patterns.

**Benefits for educational institutions:**

- **Enhanced security** protects sensitive student and faculty data by identifying and managing risky cloud apps.
- **Compliance** helps meet regulatory requirements for data protection and security.
- **Improved IT management** provides IT administrators with the tools to monitor and control cloud app usage, reducing the risk of data breaches.

**Getting started:**

1. Set up cloud discovery by navigating to the Microsoft Defender for Cloud Apps portal, selecting **Cloud Discovery**. Follow the setup instructions to start analyzing your network traffic logs.
2. Configure your log collection by setting up log collectors or integrate with existing tools like Microsoft Defender for Endpoint to automate log uploads.
3. Define custom policies to monitor and control cloud app usage based on your organization's security requirements.

**Learn more:**

- [Cloud app discovery overview](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery)
- [Compare discovery capabilities for Defender for Cloud Apps and Cloud App Discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/editions-cloud-app-security-aad)

### Office 365 Cloud App Security

Office 365 Cloud App Security, now part of Microsoft Defender for Cloud Apps, provides enhanced visibility and control over your Office 365 environment. This is beneficial for educational institutions to protect sensitive data and ensure compliance with security policies.

**Key features:**

- **Threat detection** detects threats based on user activity logs and anomaly detection. This helps identify compromised accounts and insider threats.
- **Data protection** enforces data loss prevention \(DLP\) policies to protect sensitive information. It can discover, classify, label, and protect regulated data stored in the cloud.
- **App Permissions Management** manages and controls app permissions to Office 365, ensuring that only trusted apps have access to your data.
- **Shadow IT discovery** identifies and monitors cloud apps being used within your organization, helping to manage and mitigate risks associated with unsanctioned apps.
- **Automated remediation** provides automated responses to detected threats, reducing the time to mitigate potential security issues.

**Benefits for educational institutions:**

- **Enhanced security** protects student and faculty data from cyber threats and unauthorized access.
- **Compliance** helps meet regulatory requirements for data protection and privacy.
- **Improved visibility** offers insights into user activities and app usage, enabling better security management.

**Getting started:**

1. Access the Microsoft Defender for Cloud Apps portal.
2. Configure policies for threat detection, data protection, and app permissions. Use built-in policy templates to get started quickly.
3. Regularly monitor alerts and reports in the portal. Use automated remediation actions to quickly address any detected threats.

**Learn more:**

- [How Defender for Cloud Apps helps protect your Microsoft 365 environment](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-office-365)
- [Compare Microsoft Defender for Cloud Apps and Office 365 Cloud App Security](https://learn.microsoft.com/en-us/defender-cloud-apps/editions-cloud-app-security-o365)
