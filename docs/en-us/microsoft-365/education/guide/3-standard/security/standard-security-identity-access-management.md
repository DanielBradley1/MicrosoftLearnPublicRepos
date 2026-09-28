<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/security/standard-security-identity-access-management -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 5: Identity access management

Identity access management is a critical component of cybersecurity in educational institutions. This article provides an overview of features and best practices for the A3 educational license. It covers essential tools and strategies to help IT administrators manage identities, secure access, and protect sensitive data in a school environment.

## Requirements

- Microsoft 365 A3 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Advanced security reports

Advanced security reports are crucial for educational institutions to understand and mitigate cyber threats. Here are some key aspects and benefits of these reports:

- **Threat intelligence** provides insights into the latest cyber threats targeting educational institutions, such as malware, phishing, and ransomware attacks.
- **Vulnerability assessments** identify weaknesses in the IT infrastructure, helping schools and universities prioritize security measures.
- **Compliance monitoring** ensures that the institution meets regulatory requirements and standards for data protection.
- **Incident response** offers detailed analysis of security incidents, helping institutions improve their response strategies.

**Learn more:**

- [Cyber Signals Issue 8 \| Education under siege: How cybercriminals target our schools​​](https://www.microsoft.com/security/blog/2024/10/10/cyber-signals-issue-8-education-under-siege-how-cybercriminals-target-our-schools/)

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

## Cloud user self-service password reset

To enable cloud user self-service password reset \(SSPR\) in an educational setting, you can use Microsoft Entra ID \(formerly Azure AD\). This feature allows students, faculty, and staff to reset their passwords without needing to contact IT support. Here’s how to set it up.

**Benefits in education:**

- **Reduced IT burden:** Students and staff can reset their passwords independently, reducing helpdesk tickets.
- **Improved security:** Enforces strong password policies and reduces the risk of compromised accounts.
- **Enhanced user experience:** Provides a seamless experience for users, allowing them to reset passwords from anywhere.

**Prerequisites:**

- Licensing: Ensure that your users have licenses that include SSPR capabilities, such as Microsoft 365 Education A3 or A5.
- Microsoft Entra ID: Your organization must be using Microsoft Entra ID.

**Steps to configure SSPR:**

1. Access the Microsoft Entra Admin Center.
2. To enable SSPR, navigate to **Users > Password reset**. Under *Self-service password reset*, select **Properties**. Choose **Selected** or **All** to specify which users can use SSPR, and select **Save**.
3. To configure Authentication Methods, go to **Authentication methods** under Password reset settings. Select the number of methods required to reset a password \(for example, one or two\) and choose the available methods \(for example, email, phone, security questions\). Select **Save**.
4. Ensure users register their authentication methods. They can do this by signing into the My Account portal and following the prompts to set up their security info.
5. Test the configuration by having a user test the SSPR process by going to the password reset portal. They should follow the prompts to verify their identity and reset their password.

**Learn more:**

- [Let users reset their own passwords](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/let-users-reset-passwords)
- [Reset your work or school password using security info](https://support.microsoft.com/account-billing/reset-your-work-or-school-password-using-security-info-23dde81f-08bb-4776-ba72-e6b72b9dda9e)

## Hybrid user self-service password change/reset on-premises

To enable hybrid user self-service password change/reset for on-premises environments in an educational setting, you can use Microsoft Entra ID \(formerly Azure AD\) with password writeback. This allows users to reset their passwords in the cloud, and have those changes synchronized back to your on-premises Active Directory \(AD\). Here’s how to set it up.

**Benefits in education:**

- **Reduced IT burden:** Students and staff can reset their passwords without IT intervention, reducing helpdesk tickets.
- **Improved security:** Enforces strong password policies and reduces the risk of compromised accounts.
- **Enhanced user experience:** Provides a seamless experience for users, allowing them to reset passwords from anywhere.

**Prerequisites:**

- Microsoft Entra Connect: Ensure you have Microsoft Entra Connect installed and configured.
- Licensing: Users must have licenses that include self-service password reset \(SSPR\) capabilities, such as Microsoft 365 Education A3 or A5.

**Steps to configure:**

1. Enable password writeback in Microsoft Entra Connect:

   1. Open Microsoft Entra Connect and select **Configure**.
   2. Choose **Customize synchronization options** and proceed through the wizard until you reach the **Optional Features** page.
   3. Enable **Password writeback** and complete the wizard.

2. Enable Self-Service Password Reset \(SSPR\):

   1. Go to the Microsoft Entra admin center.
   2. Navigate to **Users > Password reset**.
   3. Select **Self-service password reset** and configure the settings to enable SSPR for your users. You can choose to enable it for all users or a specific group.

3. Configure SSPR for Hybrid Users:

   1. Ensure that your Windows 10 devices are hybrid Microsoft Entra ID joined.
   2. In Intune, create a device configuration profile to enable SSPR from the Windows sign-in screen:

      1. Go to **Devices > Configuration profiles > + Create profile**.
      2. Select **Windows 10 and later** as the platform and **Templates** as the profile type.
      3. Choose **Identity protection** and configure the settings to enable SSPR.

4. Verify Configuration:

   1. Test the configuration by having a user reset their password from the Microsoft 365 portal or the Windows 10 sign-in screen.
   2. Ensure that the password change is written back to the on-premises AD.

**Learn more:**

- [How does self-service password reset writeback work in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-writeback)
