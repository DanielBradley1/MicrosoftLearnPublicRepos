<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-security-center-mde -->
<!-- Sitemap-Last-Modified: 2024-10-16 -->

# Microsoft Defender for Endpoint in the Microsoft Defender portal

[Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) is part of the Microsoft Defender portal, delivering a unified experience for security teams to manage incidents and alerts, hunt for threats, and automate investigations and responses. The Microsoft Defender portal \([https://security.microsoft.com](https://security.microsoft.com)\) combines security capabilities that protect assets, and detect, investigate, and respond to threats.

Endpoints like laptops, phones, tablets, routers, and firewalls are the entry points to your network. Microsoft Defender for Endpoint helps you secure these endpoints by providing visibility into the activities on your network, and by detecting and responding to advanced threats.

This guide shows you what to expect when running Microsoft Defender for Endpoint in the Microsoft Defender portal.

## Know before you begin

To use Microsoft Defender for Endpoint in the Microsoft Defender portal, you need to have a Microsoft Defender for Endpoint license. For more information, see [Microsoft Defender for Endpoint licensing](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements#licensing-requirements).

In addition, confirm that you have the requirements on hardware and software, browser, network connectivity, and compatibility with Microsoft Defender Antivirus. For more information, see [Microsoft Defender for Endpoint minimum requirements](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements).

You also need to have the required permissions to access the Microsoft Defender portal. For more information, see [Use basic permissions to access the portal](https://learn.microsoft.com/en-us/defender-endpoint/basic-permissions).

## What to expect

### Investigation and response

Investigation and response capabilities in the Microsoft Defender portal help you investigate and respond to incidents and alerts. Incidents are groups of alerts that are related to each other.

#### Incidents and alerts

Devices involved in incidents are shown in an incident's page [attack story](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#attack-story), incident graph, and [assets](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#assets) tab. You can view the details of the incident, including the devices involved, the alerts that triggered the incident, and the actions taken. You can apply actions to the incident, like isolating devices, collecting investigation packages, and more.

[![Screenshot of the Assets tab highlighting the devices involved in an incident.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/incident-assets-devices-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/incident-assets-devices.png#lightbox)

Individual alerts are shown in the Alerts page. You can view the details of the alert, including the devices involved, the incident that the alert is part of, and the actions taken. You can also apply actions to the alert in the alert page.

#### Hunting

Proactively search for threats, malware, and malicious activity across your endpoints, Office 365 mailboxes, and more by using [advanced hunting queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview). These powerful queries can be used to locate and review threat indicators and entities for both known and potential threats.

[Custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules) can be built from advanced hunting queries to help you proactively watch for events that might be indicative of breach activity and misconfigured devices.

#### Action center and submissions

The [Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center) shows you the investigations created by automated investigation and response capabilities. This automated self-healing in the Microsoft Defender portal can help security teams by automatically responding to specific events. You can view actions applied to devices, the status of the actions, and approve or reject the automated actions. Navigate to the Action center page under **Investigation & response > Actions & submissions > Action center**.

[![Screenshot of the Action center in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/action-center-mde-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/action-center-mde.png#lightbox)

You can submit files, email attachments, and URLs to Microsoft Defender for analysis in the [Submission portal](https://learn.microsoft.com/en-us/defender-endpoint/admin-submissions-mde). You can also view the status of the submissions and the results of the analysis. Navigate to the submissions page under **Investigation & response > Actions & submissions > Submissions**.

### Threat intelligence

You can view emerging threats, new attack techniques, prevalent malware, and information about threat actors and campaigns in the **Threat intelligence** page. Access the [threat analytics](https://learn.microsoft.com/en-us/defender-endpoint/threat-analytics) dashboard to view the latest threat intelligence and insights. You can also view read and understand how to protect from certain threats through the [analyst report](https://learn.microsoft.com/en-us/defender-endpoint/threat-analytics-analyst-reports).

Navigate to the threat analytics page under **Threat intelligence > Threat analytics**.

### Device inventory

The **Assets > Devices** page contains the [device inventory](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview), which lists all the devices in your organization where alerts were generated. You can view the details of the devices, including the IP address, criticality level, device category, and device type.

[![Screenshot of the Device inventory page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/device-inventory-mde-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/device-inventory-mde.png#lightbox)

### Microsoft Defender for Vulnerability Management and endpoint configuration management

You can find [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) dashboard under **Endpoints > Vulnerability management**. Defender for Vulnerability Management helps you discover, prioritize, and remediate vulnerabilities in your network. Know more about [prerequisites and permissions](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-prerequisites) and how to [onboard devices to Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/mdvm-onboard-devices).

The device configuration dashboard is found in **Endpoints > Configuration management > Dashboard**. You can view device security, onboarding via Microsoft Intune and Microsoft Defender for Endpoint, web protection coverage, and attack surface management at a glance.

Security administrators can deploy endpoint security policies to devices in your organization under **Endpoints > Configuration management > Endpoint security policies**. Know more about [endpoint security policies](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure).

### Reports

You can view device health, vulnerable devices, monthly security summary, web protection, firewall, device control, and attack surface reduction rules reports in the **Reports** page.

[![Screenshot of the Reports page highlighting the endpoint-related reports in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/reports-mde-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/reports-mde.png#lightbox)

### General settings

#### Device discovery

In the **Settings > Device discovery** page, you can configure device discovery settings, including the discovery method, exclusions, enabling Enterprise IOT \(access dependent\), and configure authenticated scan schedules. For more information, see [Device discovery](https://learn.microsoft.com/en-us/defender-endpoint/device-discovery).

[![Screenshot of the Device discovery page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/device-discovery-mde-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/device-discovery-mde.png#lightbox)

#### Endpoint settings

Navigate to the **Settings > Endpoints** page to configure settings for Microsoft Defender for Endpoint, including [advanced features](https://learn.microsoft.com/en-us/defender-endpoint/advanced-features), email notifications, permissions, and more.

[![Screenshot of the Settings page in the Microsoft Defender portal where endpoint settings are highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/settings-mde-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mde/settings-mde.png#lightbox)

#### Email notifications

You can create rules for specific devices, alert severities, and vulnerabilities to send email notifications to specific users or groups. For more information, see the following information:

- [Configure email notifications for alerts](https://learn.microsoft.com/en-us/defender-xdr/configure-email-notifications)
- [Configure email notifications for vulnerabilities](https://learn.microsoft.com/en-us/defender-endpoint/configure-vulnerability-email-notifications)

#### Permissions and roles

To manage roles, permissions, and device groups for endpoints, navigate to *Permissions* under **Settings > Endpoints**. You can create and define role and assign permissions under *Roles* and create and organize devices into groups under *Device groups*.

Alternately, you can navigate to *Endpoints roles & groups* in the **System > Permissions** page.

#### APIs and MSSPs

The Microsoft Defender XDR alerts API is the official API that enables customers to work with alerts across all Defender products using a single integration. For more information, see [Migrate from the MDE SIEM API to the Microsoft Defender XDR alerts API](https://learn.microsoft.com/en-us/defender-endpoint/configure-siem).

To authorize a managed security service provider \(MSSP\) to access receive alerts, you need to provide the application and tenant IDs of the MSSP. For more information, see [MSSP integration](https://learn.microsoft.com/en-us/defender-endpoint/configure-mssp-support#mssp-integration).

#### Rules

You can create rules and policies to manage indicators, filter web content, manage automation uploads and automation folder exclusions, and more. To create these rules, navigate to *Rules* under **Settings > Endpoints**. More information on managing these rules can be found in the following links:

- [Manage indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicator-manage)
- [Manage automation uploads](https://learn.microsoft.com/en-us/defender-endpoint/manage-automation-file-uploads)
- [Manage automation folder exclusions](https://learn.microsoft.com/en-us/defender-endpoint/automation-folder-exclusions-configure)
- [Filter web content](https://learn.microsoft.com/en-us/defender-endpoint/web-content-filtering)

#### Security setting management

In **Settings > Endpoints > Configuration management > Enforcement scope**, you can allow Microsoft Intune security settings to be enforced by Microsoft Defender for Endpoint. For more information, see [Use Microsoft Intune to configure and manage Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/use-intune-config-manager-microsoft-defender-antivirus).

#### Device management

You can onboard or offboard devices and run a device detection test in the **Settings > Endpoints > Device management** page. See [Onboard to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboarding) to know the steps to onboard devices. To offboard devices, see [Offboard devices](https://learn.microsoft.com/en-us/defender-endpoint/offboard-machines).

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
