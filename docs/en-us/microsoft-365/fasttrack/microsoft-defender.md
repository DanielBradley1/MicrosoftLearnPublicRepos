<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/fasttrack/microsoft-defender -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Microsoft Defender

## Zero Trust

FastTrack provides comprehensive guidance on implementing Zero Trust security principles. The Zero Trust model assumes breach and verifies each request as though it originates from an uncontrolled network. This approach ensures robust security across your networks, applications, and environment. FastTrack accomplishes this by focusing on identity, devices, applications, data, infrastructure, and networks. With FastTrack, you can confidently advance your Zero Trust security journey and protect your digital assets effectively.

With Microsoft Defender, you can implement Zero Trust principles by providing extended detection and response \(XDR\) capabilities. This includes automatically collecting, correlating, and analyzing signal, threat, and alert data from across your Microsoft 365 environment, including endpoints, email, applications, and identities. By integrating with Microsoft Sentinel, you can create a comprehensive XDR and security information and event management \(SIEM\) solution that enhances your organization's security posture.

## Microsoft Security Exposure Management

Microsoft Security Exposure Management is a security solution that provides a unified view of security posture across company assets and workloads. Security Exposure Management enriches asset information with security context that helps you to proactively manage attack surfaces, protect critical assets, and explore and mitigate exposure risk.

FastTrack provides remote guidance for:

- Prerequisite overview including role-based access control \(RBAC\) guidance.
- Overview of:

  - Identifying and managing critical assets.
  - Available 3P data connectors.
  - How to leverage attack paths, including:

    - Attack surface map.
    - Choke points.
    - Blast radius.
    - Entry points.
    - Targets.
    - Exposure map.

  - Managing exposure with security initiatives, including:

    - Security metrics.
    - Security recommendations.
    - Security events.

### Out of scope

- Overview of enterprise exposure graph schemas and operators.
- Custom enterprise exposure graph query writing.
- Identification/Creation of custom critical assets within customer environment.
- Troubleshooting 3P data connectors.
- Remediation of vulnerabilities identified in attack paths.
- Customization of security initiatives within customer environment.
- Attack simulations \(including penetration testing\).
- Diagnosis of threats and threat hunting.
- Troubleshooting issues encountered during engagement \(including networking issues\).

## Microsoft Defender XDR

Microsoft Defender XDR is a unified pre- and post-breach enterprise defense suite. Defender XDR natively coordinates detection, prevention, investigation, and response across endpoints, identities, email, and apps to provide integrated protection against sophisticated attacks.

FastTrack provides remote guidance for:

- Providing an overview of the Microsoft Defender portal.

  - Providing an overview of cross-product incidents, including focusing on what's critical by ensuring the full attack scope, impacted assets, and automated remediation actions that are grouped together.
  - Demonstrating how Microsoft Defender XDR can orchestrate the investigation of assets, users, devices, and mailboxes that become compromised through automated self-healing.
  - Explaining and providing examples of how customers can proactively hunt for intrusion attempts and breach activity affecting your email, data, devices, and accounts across multiple data sets.
  - Showing customers how they can review and improve their security posture holistically using Microsoft Security Exposure Management.

- Providing education and configuration guidance on Microsoft Defender portal.

  - Connecting of a Microsoft Sentinel workspace.
  - Review of the following capabilities within the Defender portal.

    - Search.
    - Threat management.
    - Content management.
    - Configuration.

- Providing education and configuration guidance on Defender XDR Attack Disruption and Predictive Shielding capabilities.
- Review of initiatives and recommendations in Microsoft Security Exposure Management related to Microsoft Defender XDR such as:

  - Business Email Compromise \(BEC\) Initiative.
  - CIS Foundations Initiative.
  - Ransomware Protection.

### Out of scope

- Deployment guidance or education on:

  - How to remediate or interpret the various alert types and monitored activities.
  - How to investigate a user, computer, lateral movement path, or entity.
  - Custom threat hunting.

- Security information and event management \(SIEM\) or API integration.
- Preview features.

## Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps is a multi-purpose software-as-a-service \(SaaS\) security solution. It combines SaaS security posture management, data loss prevention, app-to-app protection, and integrated threat protection to ensure holistic coverage for your apps. By adopting a SaaS security approach, you can easily identify misconfigurations. This improves your overall app posture, implements policies to protect sensitive data, and protects app-to-app scenarios to ensure that only apps have the acceptable permissions to access other app data. When you natively integrate into Microsoft Defender XDR, organizations like yours benefit from using the signal from SaaS to actively hunt in their environments and combat incidents across their apps, devices, identities, and email.

FastTrack provides remote guidance for:

- Configuring the portal, including:

  - Importing user groups.
  - Managing admin access and settings.
  - Scoping your deployment to select certain user groups to monitor or exclude from monitoring.
  - How to set up IP ranges and tags.
  - Personalizing the end-user experience with your logo and custom messaging.

- Integrating first-party services including:

  - Microsoft Defender for Endpoint.
  - Microsoft Defender for Identity.
  - Microsoft Entra ID Protection.
  - Microsoft Purview Information Protection.

- Setting up cloud discovery using:

  - Microsoft Defender for Endpoints.
  - Zscaler.
  - iboss.

- Creating app tags and categories.
- Customizing app risk scores based on your organization’s priorities.
- Sanctioning and unsanctioning apps.
- Reviewing the Defender for Cloud Apps and Cloud Discovery dashboards.
- Enabling app governance.

  - Guide the customer through the overview page and create up to five \(5\) app governance policies.

- Connecting featured apps using app connectors.
- Protecting apps with Conditional Access App Control in the Conditional Access within Microsoft Entra ID and Defender for Cloud Apps portals.
- Deploying Conditional Access App Control for featured apps.
- Using the activity and file logs.
- Managing OAuth apps.
- Reviewing and configuring policy templates.
- Providing configuration assistance with the top SaaS use cases \(including the creation or updating of up to six \(6\) policies\).
- Understanding incident correlation in the Microsoft Defender portal.
- Creating a Cloud Discovery snapshot report.
- Review of initiatives and recommendations in Microsoft Security Exposure Management related to Microsoft Defender for Cloud Apps such as the SaaS Security Initiative.

### Out of scope

- Discussions comparing Defender for Cloud Apps to other Cloud Access Security Broker \(CASB\) or SaaS security offerings.
- Configuring Defender for Cloud Apps to meet specific compliance or regulatory requirements.
- Deploying the service to a nonproduction test environment.
- Deploying Cloud App Discovery as a proof of concept.
- Setting up the infrastructure, installation, or deployment of automatic log uploads for continuous reports using Docker or a log collector.
- Supporting custom log parsers, including:

  - Unsupported formats.
  - Normalizing their logs.
  - Providing guidance on how to download their logs.

- Blocking app usage using block scripts.
- Adding custom apps to Cloud Discovery.
- Connecting custom apps with Conditional Access App Control.
- Onboarding and deploying Conditional Access App Control for any app.
- Integrating with non-Microsoft identity providers \(IdPs\) and data loss prevention \(DLP\) providers.
- Training or guidance covering advanced hunting.
- Automated investigation and remediation including Microsoft Power Automate playbooks.
- SIEM or API integration \(including Microsoft Sentinel\).

## Microsoft Defender for Endpoint

Microsoft Defender for Endpoint is a platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats.

FastTrack provides remote guidance for:

- Assessing the OS version and device management approach \(including Microsoft Intune, Microsoft Endpoint Configuration Manager, Group Policy, and non-Microsoft configurations\) as well as the status of your endpoint security software.
- Onboarding Microsoft Defender for Endpoint P1 and P2 using:

  - Defender deployment tool.
  - Local script.
  - Group Policy.<sup>5</sup>
  - Intune.
  - Configuration Manager.
  - Defender for Endpoint security settings management.<sup>5</sup>

- Providing recommended configuration guidance for Microsoft traffic to travel through proxies and firewalls, restricting network traffic for devices that aren't able to connect directly to the internet.
- Enabling the Defender for Endpoint service by explaining how to deploy an endpoint detection and response \(EDR\) agent profile using one of the supported management methods.
- Deployment guidance, configuration assistance, and education on:

  - Vulnerability management core features.
  - Attack surface reduction capabilities, including:

    - Attack surface reduction rules.
    - Controlled folder access.
    - Device control for removable media devices.<sup>5</sup>
    - Network protection.

  - Next-generation protection.
  - Endpoint detection and response.
  - Automated investigation and remediation.
  - Microsoft Defender SmartScreen configuration using Intune.
  - Device discovery.<sup>1</sup>

- Reviewing simulations and tutorials \(like practice scenarios, fake malware, and automated investigations\).
- Reviewing live response script library management.
- Overview of reporting and threat analytics features.
- Integrating Microsoft Defender for Office 365, Microsoft Defender for Identity, and Defender for Cloud Apps with Defender for Endpoint.
- Conducting walkthroughs of the Microsoft Defender portal.
- Overview of critical device asset management with Microsoft Security Exposure Management.
- Review of initiatives and recommendations in Microsoft Security Exposure Management related to Microsoft Defender for Endpoint such as:

  - Endpoint Security.
  - Critical Asset Protection.

- Onboarding and configuration of the following operating systems:<sup>4</sup>

  - Windows Server 2008 R2.
  - Windows 7.
  - Windows 8.
  - Windows 10/11, including Windows 365 Cloud PCs.
  - Windows Server 2012 R2.<sup>2</sup>
  - Windows Server 2016.<sup>2</sup>
  - Windows Server 2019.<sup>2</sup>
  - Windows Server 2022.<sup>2</sup>
  - Windows Server 2019 Core Edition.<sup>2</sup>
  - Supported macOS versions.
  - Supported Linux server distributions.
  - Android.<sup>3</sup>
  - iOS.<sup>3</sup>

<sup>1</sup> Only some aspects of device discovery are supported. For more information, see the following **Out of scope** section.

<sup>2</sup> Windows Server 2012 R2 and 2016 support is limited to onboarding and configuration of the unified agent.

<sup>3</sup> For more information, see the following **Out of scope** section for mobile threat defense details.

<sup>4</sup> For more information about integrating Defender for Endpoint with Microsoft Defender for Servers, see [Microsoft Defender for Cloud](#microsoft-defender-for-servers).

<sup>5</sup> Only some aspects of configuring Device Control are supported. For more information, see the following **Out of scope section.**

#### Out of scope

- Onboarding and enablement guidance for preview features.
- Troubleshooting issues encountered during engagement \(including devices that fail to onboard\). FastTrack directs customers to Microsoft Support for assistance.
- Supporting Microsoft Defender for Business.
- Onboarding or configuration for the following Defender for Endpoint agents:

  - Any operating system or device type not supported by Defender for Endpoint.
  - Linux distributions not supported by Defender for Endpoint.
  - Linux instances using customized kernels.
  - Windows Subsystem for Linux \(WSL\).
  - Virtual Desktop Infrastructure \(VDI\) \(persistent or non-persistent\), including Azure Virtual Desktop and non-Microsoft VDI solutions.

- Server onboarding and configuration.

  - Configuring a proxy server for offline communications.
  - Configuring Configuration Manager deployment packages on down-level Configuration Manager instances and versions.
  - Servers not managed by Configuration Manager or Defender for Endpoint security settings management.

- Linux server onboarding and configuration.

  - Prescriptive assistance with any non-Microsoft systems management tools or products \(including development of configuration files associated with them\), including:

    - Chef
    - Puppet.
    - Ansible.
    - Saltstack.

  - FastTrack refers customers to applicable technical guidance whenever possible.

- macOS onboarding and configuration.

  - JAMF-based deployment.
  - Other mobile device management \(MDM\) product-based deployment.
  - Manual deployment.

- Mobile threat defense onboarding and configuration \(Android and iOS\).

  - Unmanaged bring your own devices \(BYOD\) or devices managed by other enterprise mobility management systems.
  - Set up app protection policies \(like mobile app management \(MAM\)\).

    - Android devices.
    - Admin-enrolled devices.

  - Assistance with coexistence of multiple VPN profiles.
  - Onboarding devices to Intune. For more information on onboarding assistance, see [Microsoft Intune](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/microsoft-intune).

- Configuration of the following attack surface reduction capabilities:

  - Hardware-based application and browser isolation \(including Application Guard\).
  - Application control, including AppLocker and Windows Defender Application Control.
  - The following device control functions:

    - Device installation restrictions.
    - Data protection.
    - Storage.
    - Windows Portable Devices \(WPD\) removable storage access.
    - Connectivity.
    - Bluetooth.
    - Direct Memory Access \(DMA\) guard.

  - Exploit protection.
  - Network and endpoint firewalls.

- Configuration or management of account protection features like:

  - Credential Guard.
  - Local user group membership.

- Configuration or management of BitLocker.
- Configuring MDE Device Control via Group Policy \(GPO\).

Note

For information on BitLocker assistance with Windows 11, see [Windows 11](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/windows-and-app-assure).

- Configuration or management of network device discovery.
- Configuration or management of the following device discovery capabilities:

  - Onboarding of unmanaged devices not in scope for FastTrack \(like Linux\).
  - Configuring or remediating internet-of-things \(IoT\) devices including vulnerability assessments of IoT devices through Defender for IoT.
  - Integration with non-Microsoft tooling.
  - Exclusions for device discovery.
  - Preliminary networking assistance.
  - Troubleshooting network issues.

- Attack simulations \(including penetration testing\).
- Enrollment or configuration of Microsoft Threat Experts.
- Configuration or training guidance for API or SIEM connections.
- Training or guidance covering advanced hunting.
- Training or guidance covering the use of or creation of Kusto queries.
- Training or guidance covering Defender SmartScreen configuration using Group Policy Objects \(GPOs\), Windows Security, or Microsoft Edge.
- Defender Vulnerability Management Add-on.
- Defender Vulnerability Management Standalone.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with these services.

## Microsoft Defender for Identity

Microsoft Defender for Identity is a cloud-based security solution. It uses your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.

FastTrack provides remote guidance for:

- Running the sizing tool for resource capacity planning.
- Creating your instance of Defender for Identity.
- Configuring Windows event collection across Active Directory Domain Services \(AD DS\), Active Directory Federation Services \(AD FS\), Active Directory Certificate Services \(AD CS\), and Microsoft Entra Connect.
- Managing admin access with role groups.
- Deploying or activating, and configuring the sensor \(Classic V2 and Unified V3\) on your Active Directory domain controllers for both single and multiple forest environments.
- Migrating from Classic V2 to Unified V3.
- Creating and configuring directory service accounts or manage action accounts in Active Directory including group managed service accounts \(gMSA\).
- Downloading, deploying, and configuring the sensor on your AD FS, AD CS, and Microsoft Entra Connect servers.
- Portal configuration, including:

  - Tagging sensitive accounts, devices, or groups.
  - Email notifications for health issues and security alerts.
  - Alert exclusions.
  - Scheduled reports.

- Providing deployment guidance, configuration assistance, and education on:

  - Inactive user reports.
  - Remediation options on a compromised account.

- Facilitating the migration from Advanced Threat Analytics \(ATA\) to Defender for Identity \(if applicable\).
- Overview of critical identity asset management with Microsoft Security Exposure Management
- Review of initiatives and recommendations in Microsoft Security Exposure Management related to Microsoft Defender for Identity such as:

  - Identity Security Initiative
  - Critical Asset Protection Initiative

### Out of scope

- Deploying Defender for Identity as a proof of concept.
- Deploying or performing the following Defender for Identity sensor activities:

  - Manual capacity planning.
  - Deploying the standalone sensor.
  - Deploying the sensor using a Network Interface Card \(NIC\) Teaming adaptor.
  - Deploying the sensor through a non-Microsoft tool.
  - Connecting to the Defender for Identity cloud service through a web proxy connection.

- Disabling Microsoft Defender for Identity service.
- Creating and configuring permissions for the AD FS database.
- Creating and configuring permissions for Microsoft Entra Connect for use with an ADSync database.
- Creation and management of honeytokens accounts or devices.
- Enabling Network Name Resolution \(NNR\).
- Enabling and configuration of the Deleted Objects container.
- Deployment guidance or education on:

  - Remediating or interpreting various alert types and monitored activities.
  - Investigating a user, computer, lateral movement path, or entity.
  - Threat or advanced hunting.
  - Incident response.

- Providing a security alert lab tutorial for Defender for Identity.
- Providing notification when Defender for Identity detects suspicious activities by sending security alerts to your syslog server through a nominated sensor.
- Configuring Defender for Identity to perform queries using security account manager remote \(SAMR\) protocol to identify local admins on specific machines.
- Configuring VPN solutions to add information from the VPN connection to a user’s profile page.
- SIEM or API integration \(including Microsoft Sentinel\).

### Source environment expectations

- Aligned with Defender for Identity prerequisites.
- Active Directory, AD FS, AD CS, and Microsoft Entra Connect deployed.
- The Active Directory domain controllers you intend to install Defender for Identity sensors on have internet connectivity to the Defender for Identity cloud service.

  - Your firewall and proxy must be open to communicate with the Defender for Identity cloud service \(\*.atp.azure.com port 443 must be open\).

- Domain controllers running on one of the following servers:

  - Windows Server 2016.
  - Windows Server 2019 with KB4487044 \(OS Build 17763.316 or later\).
  - Windows Server 2022.
  - Windows Server 2025.

- Microsoft .NET Framework 4.7 or later.
- A minimum of six \(6\) GB of disk space is required and 10 GB is recommended.
- Two \(2\) cores and six \(6\) GB of RAM installed on the domain controller.

## Microsoft Defender for Office 365

Microsoft Defender for Office 365 safeguards your organization against malicious threats posed by email messages, links \(URLs\), attachments, and collaboration tools like Microsoft Teams, SharePoint, and Outlook. With real-time views of threats and tools like Threat Explorer, you can hunt and stay ahead of potential threats. Use attack simulation training to run realistic attack scenarios in your organization. These simulated attacks can help you identify and find vulnerable users before a real attack impacts your bottom line.

FastTrack provides remote guidance for:

- Reviewing the Configuration analyzer and/or Defender for Office 365 Recommended Configuration Analyzer \(ORCA\).
- Setting up evaluation mode.
- Enabling preset policies, Safe Links \(including Safe Documents\), Safe Attachments, anti-malware, anti-phishing, anti-spam, anti-spoofing, impersonation, and quarantine policies.
- Providing an overview of priority accounts and user tags.
- Defining spam and bulk user experiences.
- Enabling Teams protection.
- Configuring user-reported message settings.
- Using Attack simulation training and configuring an advanced delivery policy.
- Providing an overview of the Tenant Allow/Block List \(TABL\), submissions, email entity page, reporting, campaigns, threat explorer, and threat analytics.
- Providing an overview of spoof intelligence, impersonation protection, and mailbox intelligence.
- Providing an overview of zero-hour auto purge \(ZAP\) automated investigation and response \(AIR\).
- Understanding incident correlation in the Microsoft Defender portal.
- Understanding the impact of features that modify messages and external tags.
- Transitioning from a non-Microsoft provider following the Microsoft best practice guidance except for creating an inventory of your current settings.
- Providing an overview of mail flow analysis.

### Out of scope

- Discussions comparing Defender for Office 365 to other security offerings.
- Deploying Defender for Office 365 as a proof of concept.
- Training or guidance covering advanced hunting.
- Integration with Microsoft Power Automate playbooks.
- SIEM or API integration \(other than Microsoft Sentinel\).

### Source environment expectations

In addition to [FastTrack core onboarding](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/products-and-capabilities#fasttrack-core-onboarding), [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#exchange-online) must also be configured.

## Microsoft Defender for Servers

Microsoft Defender for Server is a workload protection service in Microsoft Defender for Cloud. Microsoft Defender for Cloud is a cloud-native application protection platform \(CNAPP\) that's made up of security measures and practices designed to protect cloud-based applications from various cyber threats and vulnerabilities.

FastTrack helps you extend your protection of cloud workloads by deploying Microsoft Defender for Servers on Windows and Linux Servers that run in Microsoft Azure, on-premises, and other clouds. Defender for Servers integrates with Microsoft Defender for Endpoint to provide endpoint detection and response \(EDR\) and other threat protection features.

FastTrack provides remote guidance for:

- An overview of Defender for Server, including:

  - Scoping pre-deployment best practices.

    - Ensuring the basic environment setup and knowledge is in place.
    - Helping customers understand onboarding methods \(*Direct vs. Azure Arc*\) and the feature/benefit impact.
    - Defining and implementing a management group hierarchy in the Azure environment.
    - Limited support - Deploying features Defender for Server on servers that run in Amazon Web Services \(AWS\) and Google Cloud Platform \(GCP\).

  - Validating roles and permissions.

    - Creating a device group in MDE to support management of the onboarded devices & limit access to customer's server management team.

  - Server onboarding.

    - Providing guidance to customers on how to enable Azure Arc on a pilot server in their environment.
    - Assisting customer’s team in scaling onboarding Servers to Defender for Server.
    - Providing limited guidance for use of Azure Policy to use with deployment of Defender for Servers.
    - Providing guidance for Direct Onboarding.

### Out of scope

- Detailed pricing information. Contact your account team for more information.
- MDC Components that are not Defender for Server \(Defender for API, Containers, Storage, etc.\)
- Configuring AWS or GCP environments beyond the Azure-side onboarding. This includes setting up projects, stacks, or connectors within AWS or GCP.
- Deployment relying on Azure APIs for onboarding Defender for Servers.
- Deploying Defender for Server features, including:

  - Deploying agentless scanning for both Defender for Cloud Foundational CSPM and Defender for Servers.
  - Enabling File Integrity Monitoring \(FIM\) through the Defender for Endpoint sensor.
  - Customizing and optimizing FIM.
  - Configuring just-in-time virtual machine access.
  - Managing Azure Update Manager remediation for Azure Arc devices.
  - Managing free data ingestion using Azure Monitor Agent \(AMA\) to ingest logs.
  - Deploying the Microsoft Defender Vulnerability Management add-on.
  - Configuring security policy and regulatory compliance.
  - Managing docker host hardening.
  - Deploying a network map.

## Copilot in Defender

FastTrack provides remote guidance for:

- Onboarding assistance, including:

  - Provisioning Security Compute Units \(SCUs\).

Note

All M365 E5 customer tenants are automatically provisioned and onboarded to Security Copilot

- Configuring default environments with necessary roles and permissions and enabling Security Copilot embedded experiences.
- Walkthroughs for Security Copilot in Defender, including:

  - Incident summaries, guided responses, and incident reports.
  - Identity and device summaries.
  - File and script analyzer guidance.
  - Natural language to Kusto Query Language \(KQL\) overview and demonstration.
  - Defender Threat Intelligence \(Defender TI\) prompting.

- Walkthroughs of Copilot in Defender agentic AI experiences, including:

  - Demonstrating how agentic AI assists Defender workflows by summarizing incidents, device and identity information and activity.
  - Showing how agentic experiences reduce analyst effort and decision fatigue by analyzing scripts and files and recommending next actions.
  - Simplifying hunting experiences with natural language to KQL \(NL2KQL\)
  - Walking through realistic security scenarios to illustrate where and when Microsoft agents can be invoked.
  - Providing guidance on prerequisites, roles, and permissions required to enable and use agentic experiences in Defender.

### Out of scope

- Detailed pricing information. Contact your account team for more information.
- Threat hunting and incident responses.
- Providing walkthroughs of Security Copilot standalone experiences.
- Creating new custom agents.
- Deploying third party agents.

### Microsoft advanced deployment guides

Microsoft provides customers with technology and guidance to assist with deploying your Microsoft 365, Microsoft Viva, and security services. We encourage our customers to start their deployment journey with [these](https://go.microsoft.com/fwlink/?linkid=2247725) offerings.

For non-IT admins, see [Microsoft 365 Setup](https://go.microsoft.com/fwlink/?linkid=2247454).

Note

If deployment guidance for a product is not listed in the FastTrack service, complete the Request for Assistance form, to ensure you’re directed to the most appropriate resources for your deployment goals and organizational needs. Once submitted, your request will be reviewed and routed to a resource who can best support your deployment goals.

Note

*Please note that the scope and SLA of support may vary depending on the specific workload. FastTrack can help recommend resources from self-guidance, Microsoft Unified offerings, or Microsoft partners to meet your deployment needs.*
