<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/security/standard-security-cloud-access -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 1: Cloud access security broker

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

In today's digital age, educational institutions face unique challenges in securing cloud access and protecting sensitive data. This article provides an overview of the Cloud Access Security Broker \(CASB\) solutions available with Microsoft 365 A3 license for education. It highlights the features, benefits, and best practices for implementing Microsoft Defender for Cloud Apps and Office 365 Cloud App Security to ensure a secure and compliant cloud environment for schools and universities.

## Requirements

- Microsoft 365 A3 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Defender for Cloud Apps

| Feature | Description | Learn more Links |
| --- | --- | --- |
| **Defender for Cloud Apps Discovery** | Subset of Microsoft Defender for Cloud Apps. It includes cloud discovery capabilities that provide deeper visibility into cloud app usage in your organizations. | [Compare discovery capabilities for Defender for Cloud Apps and Cloud App Discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/editions-cloud-app-security-aad) |
| **Office 365 Cloud App Security** | Subset of Microsoft Defender for Cloud Apps that provides enhanced visibility and control for Office 365. Includes threat detection based on user activity logs, discovery of Shadow IT for apps that have similar functionality to Office 365 offerings, control app permissions to Office 365, and apply access and session controls. | [Compare Microsoft Defender for Cloud Apps and Office 365 Cloud App Security](https://learn.microsoft.com/en-us/defender-cloud-apps/editions-cloud-app-security-o365) |

## Microsoft Defender for Cloud Apps Discovery

Microsoft Defender for Cloud App Discovery is a powerful tool tailored to enhance cybersecurity in educational institutions by providing comprehensive visibility into cloud application usage. In the context of education, where various cloud-based tools and applications are often employed to facilitate teaching, learning, and administration, the need for secure and compliant application usage is paramount. Defender for Cloud App Discovery enables educational IT administrators to detect shadow IT by identifying unsanctioned applications being accessed by students, teachers, or staff. It offers actionable insights into user activity, data movement, and potential risks associated with noncompliant apps. This helps institutions enforce policies that safeguard sensitive data, such as student records or intellectual property, while ensuring compliance with regulations like FERPA. By integrating with Microsoft 365, it empowers schools and universities to foster a secure digital learning environment, protecting both users and data.

**Key features:**

- **Cloud app visibility**

  - Discover all cloud apps in use within the organization, even if unsanctioned.
  - Identify shadow IT applications.
  - Provide insights into usage patterns and associated risks.

- **Risk assessment**

  - Evaluate apps based on 90+ risk factors such as compliance, security, and user behavior.
  - Assign risk scores to help prioritize actions.

- **Compliance monitoring**

  - Ensure compliance with regulatory standards like FERPA and COPPA.
  - Identify apps that might compromise sensitive educational data.

- **Integration with Microsoft 365**

  - Seamless integration with Microsoft 365 for enhanced visibility and control.
  - Simplified policy enforcement for apps used by students, faculty, and staff.

- **Real-time threat detection**

  - Detect unusual activity or threats in real time.
  - Protect data against breaches or leaks using AI-powered analytics.

**Benefits for education:**

- **Enhanced security**

  - Protect student, staff, and institutional data from unauthorized access or misuse.
  - Mitigate risks associated with third-party apps.

- **Informed decision making**

  - Data-driven insights into app usage and risks.
  - Help IT administrators take informed actions to secure the digital environment.

- **Regulatory compliance**

  - Simplifies adherence to education-specific compliance standards.
  - Reduce the risk of fines or reputational damage due to noncompliance.

- **Ease of implementation**

  - Designed for ease of use in educational settings. Quick deployment and integration with existing infrastructure.

**Use cases in education:**

- **Shadow IT discovery** - Identify and mitigate unsanctioned app usage by students or staff.
- **Risk management** - Address potential security risks posed by external apps and proactively block high-risk apps.
- **Policy enforcement** - Apply policies to restrict usage of apps that don't meet institutional guidelines.
- **Incident response** - Quickly respond to breaches or suspicious activity.

**Getting started:**

1. **Set up**: Enable Microsoft Defender for Cloud App Discovery via the Microsoft 365 Admin Center.
2. **Integrate logs**: Configure data collection from firewalls, proxies, or other network devices.
3. **Analyze data**: Review app usage and risks using the dashboard.
4. **Implement policies**: Block or sanction apps based on risk assessments.
5. **Monitor and adjust**: Continuously monitor and refine policies to maintain security.

**Resources:**

- [Microsoft Security Blog](https://www.microsoft.com/security/blog/)

## Office 365 Cloud App Security

Office 365 Cloud App Security \(MCAS\) is a robust tool designed to enhance cybersecurity in educational institutions by providing visibility, control, and protection over cloud-based applications and services. It empowers schools and universities to safeguard sensitive student and staff data while ensuring compliance with regulatory requirements like FERPA. With advanced threat detection, it identifies and mitigates risks such as unauthorized access, data leaks, and malware attacks. The platform's real-time monitoring and analytics allow IT administrators to track user activities, detect suspicious behavior, and enforce policies like conditional access and data loss prevention \(DLP\). By integrating seamlessly with Office 365 and other applications, MCAS supports a secure learning environment, enabling educators and students to collaborate effectively without compromising data security.

**Key features:**

- **Cloud discovery**

  - Identifies and monitors usage of cloud applications.
  - Helps detect shadow IT within the institution.
  - Analyzes risk levels of applications used by students and staff.

- **Threat protection**

  - Detects and mitigates threats like compromised accounts and insider threats.
  - Uses machine learning and anomaly detection to identify unusual behavior.
  - Provides alerts for suspicious activities \(for example, unusual sign-in locations, data exfiltration\).

- **Information protection**

  - Ensures sensitive data \(for example, student records, research data\) is secure.
  - Integrates with Microsoft Information Protection \(MIP\) for labeling and protecting sensitive documents.
  - Offers session controls to limit data exposure in real time.

- **Compliance and governance**

  - Assists in meeting FERPA, HIPAA, GDPR, and other compliance standards.
  - Provides activity reports to ensure audit readiness.
  - Allows custom policies to enforce institutional data governance rules.

**Benefits for educational institutions:**

- **Enhanced security**

  - Protects against phishing, malware, and data leaks.
  - Reduces the risk of account takeovers and unauthorized access.

- **Visibility and control**

  - Tracks application usage across the organization.
  - Provides detailed insights into user activity and potential vulnerabilities.

- **Customizable policies**

  - Enables institutions to define and enforce security policies tailored to their needs.
  - Offers conditional access controls to regulate app and data usage.

- **Cost-effectiveness**

  - Eliminates the need for additional third-party solutions by integrating into the existing Microsoft ecosystem.

**Use cases in education:**

- **Protecting student and staff data**

  - Automatically detects sensitive data being shared externally.
  - Prevents unauthorized downloads of protected documents.

- **Enabling secure remote learning**

  - Monitors cloud usage during virtual classes.
  - Protects against unauthorized access to learning management systems.

- **Combating shadow IT**

  - Identifies non-sanctioned applications used by students and staff.
  - Provides risk analysis for third-party apps and services.

**Deployment and integration:**

- Easily integrates with Microsoft 365 applications like Teams, SharePoint, and OneDrive.
- Supports seamless integration with third-party cloud apps for broader security coverage.
- Requires minimal technical expertise for deployment in education environments.

**Best practices:**

- **Educate staff and students** - Conduct training on recognizing phishing and safe online behavior.
- **Implement conditional access policies** - Restrict access based on location, device, or user role.
- **Regular monitoring** - Use dashboards to track cloud usage and detect anomalies.
- **Leverage automation** - Automate responses to common security threats for faster remediation.

**Learn more:**

- [Microsoft Defender for Cloud Apps](https://www.microsoft.com/security/business/cloud-app-security)

## App governance in Defender for Cloud Apps

App governance in Defender for Cloud Apps is a set of security and policy management capabilities designed for OAuth-enabled apps registered on Microsoft Entra ID, Google, and Salesforce. This feature is beneficial in educational environments where the use of various applications and platforms is prevalent.

**Key features and benefits:**

- Visibility: App governance provides visibility into how apps and their users access, use, and share sensitive data in Microsoft 365 and other cloud platforms. It enables institutions to see which user-installed OAuth applications have access to data on Microsoft 365, Google Workspace, and Salesforce.
- Governance: Institutions can create proactive or reactive policies for app and user patterns and behaviors. This helps protect users from using noncompliant or malicious apps and limits the access of risky apps to sensitive data.
- Detection: App governance alerts and notifies administrators when there are anomalies in app activity or when noncompliant, malicious, or risky apps are used.
- Remediation: Along with automatic remediation capabilities, administrators can use remediation controls to respond to anomalous app activity detections in a timely manner.
- Integration: App governance data can be viewed together with other Defender for Cloud Apps data and Microsoft Entra data, allowing for aggregated information and seamless navigation between views.

**Configuration and implementation:**

- Creating access policies: Administrators can create access policies to block or restrict apps that present significant risks. This involves setting up policies in the Microsoft Entra admin center and ensuring that users in scope log on to get the policy.
- Monitoring and reporting: App governance provides detailed monitoring and reporting capabilities, allowing IT teams to track app activities and analyze trends over time.
