<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Microsoft Defender for Cloud Apps overview

Tip

You might be looking for Microsoft 365 Cloud App Security. For more information, see [What are the differences between Microsoft Defender for Cloud Apps and Microsoft 365 Cloud App Security?](https://learn.microsoft.com/en-us/defender-cloud-apps/editions-cloud-app-security-o365)

Software as a service \(SaaS\) apps are ubiquitous across hybrid work environments, and protecting SaaS apps and the important data they store is a big challenge for organizations. The rise in app usage, combined with employees accessing company resources outside of the corporate perimeter has also introduced new attack vectors. To combat these attacks effectively, security teams need an approach that protects their data within cloud apps beyond the traditional scope of cloud access security brokers \(CASBs\).

![Diagram of the Defender for Cloud App pillars.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/overview/defender-for-cloud-apps-pillars.png)

Microsoft Defender for Cloud Apps delivers full protection for SaaS applications, helping you monitor and protect your cloud app data across the following feature areas:

- **Fundamental cloud access security broker \(CASB\) functionality**, such as Shadow IT discovery, visibility into cloud app usage, protection against app-based threats from anywhere in the cloud, and information protection and compliance assessments.
- **SaaS Security Posture Management \(SSPM\) features**, enabling security teams to improve the organization’s security posture
- **Advanced threat protection**, as part of Microsoft's extended detection and response \(XDR\) solution, enabling powerful correlation of signal and visibility across the full kill chain of advanced attacks
- **App-to-app protection**, extending the core threat scenarios to OAuth-enabled apps that have permissions and privileges to critical data and resources.

## Discover SaaS applications

Defender for Cloud Apps shows the full picture of risks to your environment from SaaS app usage and resources, and gives you control of what’s being used and when.

- **Identify**: Defender for Cloud apps uses data based on an assessment of network traffic and an extensive app catalog to identify apps accessed by users across your organization. Defender for Cloud Apps provides details on which apps are really being used both on and off your corporate network.

  Defender for Cloud Apps detects all your cloud services, assigns each a risk ranking, and also identifies all the users and third-party apps able to sign in.
- **Assess**: Evaluate discovered apps for more than 90 risk indicators, allowing you to sort through the discovered apps and assess your orgs security and compliance posture.
- **Manage**: Set policies that monitor apps around the clock. For example, if anomalous behavior happens, like unusual spikes in usage, you're automatically alerted and guided to action.

For more information, see [Set up cloud discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery).

## SaaS Security Posture Management \(SSPM\)

While optimizing an organization's security posture is a critical focus area, security teams are challenged by needing to research best practices for each app individually. Defender for Cloud Apps helps you by surfacing misconfigurations and recommending specific actions to strengthen the security posture for each connected app. Recommendations are based on industry standards like the Center for Internet Security and follow best practices set by the specific app provider.

Defender for Cloud Apps automatically provides SSPM data in Microsoft Secure Score, for any supported and connected app. For more information, see [User, app governance, and security configuration visibility](https://learn.microsoft.com/en-us/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps#user-app-governance-and-security-configuration-visibility).

## Information protection

Defender for Cloud Apps identifies and helps you control sensitive information with data loss protection \(DLP\) features, and helps you respond to sensitivity labels on detected content.

The Defender for Cloud Apps integration with Microsoft Purview also enables security teams to leverage out-of-the-box data classification types in their information protection policies. Microsoft provides an expansive suite of data loss protection capabilities to ensure your data is protected no matter where it is being accessed.

Defender for Cloud Apps connects to SaaS apps to scan for files containing sensitive data uncovering which data is stored where and who is accessing it. To protect this data, organizations can implement controls such as:

- Apply a sensitivity label
- Block downloads to an unmanaged device
- Remove external collaborators on confidential files

For more information, see [Integrate Microsoft Purview Information Protection](https://learn.microsoft.com/en-us/defender-cloud-apps/azip-integration).

## Continuous threat protection in eXtended detection and response \(XDR\)

While cloud apps continue to be a target for adversaries trying to exfiltrate corporate data, sophisticated attacks often cross modalities—moving laterally from email as the most common entry point, to compromise endpoints and identities, before ultimately gaining access to in-app data.

Defender for Cloud Apps offers built-in adaptive access control \(AAC\), provides user and entity behavior analysis \(UEBA\), and helps you mitigate malware.

Defender for Cloud Apps is also integrated directly into Microsoft Defender, correlating cross-domain signals from the Microsoft Defender suite and providing incident-level detection, investigation, and powerful response capabilities. Integrating SaaS security into Microsoft's unified security experience gives SOC teams full kill chain visibility and improves operational efficiency and effectivity.

For more information, see [Microsoft Defender for Cloud Apps in Microsoft Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-security-center-defender-cloud-apps).

## App to app protection with app governance

OAuth apps often behave unnoticed, while still having extensive permissions to access data in other apps on behalf of an employee, making OAuth apps susceptible to a compromise.

Defender for Cloud Apps closes the gap on OAuth app security, helping you protect inter-app data exchange with application governance. Watch for unused apps and monitor both current and expired credentials to govern the apps used in your organization and maintain app hygiene.

For more information, see [App governance in Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance).

## Next steps

For more information, see:

- [What are the differences between Microsoft Defender for Cloud Apps and Microsoft 365 Cloud App Security?](https://learn.microsoft.com/en-us/defender-cloud-apps/editions-cloud-app-security-o365)
- [Microsoft 365 licensing datasheet](https://aka.ms/M365EnterprisePlans)
- [Getting started with Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/get-started)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
