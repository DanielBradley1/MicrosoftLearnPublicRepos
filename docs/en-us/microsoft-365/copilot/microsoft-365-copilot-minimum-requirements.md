<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Microsoft Copilot requirements

Before you deploy Microsoft Copilot or make Microsoft Copilot Chat available in your organization, review the requirements in this article. Requirements vary based on the Copilot experience and Microsoft 365 app that your users access.

Note

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. The primary URL for accessing the updated Copilot app is changing to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [Network requirements](#network-requirements) \(in this article\).

## Requirements at a glance

The following table summarizes requirements for Microsoft Copilot and Microsoft Copilot Chat. For more information about the differences between these experiences, see [Compare Copilot Chat to Microsoft Copilot](https://learn.microsoft.com/en-us/copilot/overview#compare-copilot-chat-to-microsoft-copilot).

| Category | [Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview)  <br>\(formerly Microsoft 365 Copilot\) | [Microsoft Copilot Chat](https://learn.microsoft.com/en-us/copilot/overview)  <br>\(formerly Microsoft 365 Copilot Chat\) |
| --- | --- | --- |
| [Eligible Microsoft 365 subscription or base license](#licensing-requirements) | Required | Required |
| [Microsoft Copilot license](#licensing-requirements) | Required for licensed Microsoft Copilot capabilities | Not required for eligible users |
| [Microsoft Entra ID account](#identity-and-sign-in-requirements) | Required | Required |
| [Exchange Online mailbox](#mailbox-requirements) | Required for mailbox-grounded experiences | Required only for experiences that use mailbox data |
| [Supported Microsoft 365 apps and services](#microsoft-365-app-and-service-requirements) | Required for app-specific experiences | Required for app-specific experiences |
| [Supported browser and cookies](#browser-and-cookie-requirements) | Required for web-based experiences | Required for web-based experiences |
| [Microsoft 365 and Copilot network requirements](#network-requirements) | Required | Required |
| [Secure & governed foundation](#secure-and-governed-foundation) | Recommended | Recommended |
| [Web search](#web-search-requirements) | Configurable | Configurable |

Note

Chat experiences in Word, Excel, and PowerPoint vary depending on the user's license and tenant configuration. For an overview of the available experiences, see [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview#copilot-features-in-microsoft-365-apps).

## Licensing requirements

| Experience | License requirement |
| --- | --- |
| Microsoft Copilot | Users need a Microsoft Copilot license and a qualifying prerequisite license. For the current list of eligible plans, see [License options for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing) and the [Microsoft Copilot service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-copilot).  <br>  <br>Microsoft Copilot isn't available with device-based licensing for Microsoft 365 Apps for enterprise. |
| Microsoft Copilot Chat | Microsoft Copilot Chat is available to users with an eligible Microsoft 365 subscription. For the current eligibility details, see [Microsoft Copilot Chat eligibility](https://learn.microsoft.com/en-us/copilot/manage#microsoft-copilot-chat-eligibility). |

## Identity and sign-in requirements

Users must have a work or school account in Microsoft Entra ID. You can add or synchronize users by using the [onboarding wizard in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=m365setup#/modernonboarding/identitywizard).

For administrative access, assign roles based on the tasks an administrator needs to perform. The AI Administrator role provides access to Copilot and AI administration capabilities without requiring Global Administrator permissions. For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Mailbox requirements

Microsoft Copilot supports primary mailboxes hosted in Exchange Online. Copilot can also use content that a user is permitted to access in archive, shared, and delegate mailboxes.

An Exchange Online mailbox is required for experiences that use email, calendar, meeting, or other mailbox data. The availability of a specific experience can also depend on the app, license, and tenant configuration.

Microsoft Copilot isn't available in group mailboxes.

## Microsoft 365 app and service requirements

Deploy and configure the Microsoft 365 apps and services that provide the Copilot experiences your organization plans to use.

| Apps | Description |
| --- | --- |
| [Microsoft 365 Apps](https://learn.microsoft.com/en-us/microsoft-365-apps/deploy/about-microsoft-365-apps) | Deploy Microsoft 365 Apps to users who need Copilot in desktop apps. Use the [Microsoft 365 Apps setup guide in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=learndocs#/modernonboarding/microsoft365copilotsetupguide).  <br>  <br>Review the privacy controls for connected experiences. These controls can affect the availability of Copilot features. For more information, see [Microsoft Copilot and privacy controls for connected experiences](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#microsoft-copilot-and-privacy-controls-for-connected-experiences).  <br>  <br>The Office Feature Updates task must run on its regular schedule and reach the required network resources for core Copilot experiences in apps such as Word, Excel, PowerPoint, and OneNote. For more information, see [Office Feature Updates task description and FAQ](https://learn.microsoft.com/en-us/microsoft-365/troubleshoot/updates/office-feature-updates-task-faq). |
| [OneDrive](https://learn.microsoft.com/en-us/sharepoint/onedrive-overview) | Some Copilot features require the user to have a OneDrive account. Use the [OneDrive setup guide in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=m365setup#/modernonboarding/onedrivequickstartguide) to configure OneDrive for your users. |
| [Outlook](https://learn.microsoft.com/en-us/microsoft-365-apps/outlook/overview-new-outlook-windows) | Microsoft Copilot works with supported versions of classic Outlook and new Outlook for Windows and Mac. The user must have an Exchange Online mailbox for mailbox-grounded experiences. |
| [Teams](https://learn.microsoft.com/en-us/microsoftteams/) | Copilot in Teams is available on supported Windows, Mac, web, Android, and iOS clients.  <br>  <br>To allow Copilot to reference meeting content after a meeting ends, configure transcription or recording. For more information, see [Configure transcription and captions for Teams meetings](https://learn.microsoft.com/en-us/microsoftteams/meeting-transcription-captions) and [Teams meeting recording](https://learn.microsoft.com/en-us/microsoftteams/meeting-recording). |
| [Teams Phone](https://learn.microsoft.com/en-us/microsoftteams/what-is-phone-system-in-office-365) | Copilot in Teams Phone supports voice over Internet Protocol \(VoIP\) and public switched telephone network \(PSTN\) calls.  <br>  <br>- A Microsoft Copilot license is required for Copilot support in VoIP calls.  <br>- A Teams Phone license, calling plan, and Microsoft Copilot license are required for Copilot in PSTN calls.  <br>- Transcription or recording must be enabled for Copilot to use call content.  <br>  <br>Participants receive the applicable transcription or recording notification. |
| [Loop](https://support.microsoft.com/loop/get-started-with-microsoft-loop) | To use Microsoft Copilot with Microsoft Loop, enable Loop for your tenant. For more information, see [Manage Loop workspaces in SharePoint Embedded](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-workspaces-configuration) and [Enable or disable Loop workspaces in your organization](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-workspaces-configuration). |
| [Whiteboard](https://www.microsoft.com/microsoft-365/microsoft-whiteboard/digital-whiteboard-app) | To use Microsoft Copilot with Microsoft Whiteboard, enable Whiteboard for your tenant. For more information, see [Manage access to Microsoft Whiteboard for your organization](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-whiteboard-access-organizations). |

## Browser and cookie requirements

Use a current, supported browser. Microsoft Edge, Google Chrome, Mozilla Firefox, and Apple Safari are supported for Microsoft 365 web experiences.

For Copilot to work in Word for the web, Excel for the web, and PowerPoint for the web, third-party cookies must be enabled.

## Mobile requirements

Use a supported version of the Microsoft 365 or Copilot mobile app and a supported mobile operating system. For current operating system requirements, see the app listing in the Apple App Store or Google Play Store and the applicable Microsoft 365 mobile app documentation.

## Network requirements

Copilot experiences use Microsoft 365 network connections and endpoints. Configure your network so that required Microsoft 365 and Copilot traffic isn't blocked or altered in ways that prevent the service from working.

### Microsoft 365 and Copilot endpoints

- Allow the [worldwide Microsoft 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).
- Add the [Microsoft Copilot endpoints to your allow list](https://learn.microsoft.com/en-us/microsoft-365/copilot/add-copilot-endpoints-allowlist).
- Follow [Microsoft 365 network connectivity principles and best practices](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles).

### The cloud.microsoft domain

Add `*.cloud.microsoft` to your organization's allow lists on devices and network infrastructure. Verify that URL filtering, proxy policies, firewall rules, tenant restrictions, Conditional Access policies, and app control policies don't block `copilot.cloud.microsoft` or the Copilot app.

Microsoft doesn't support allowing only selected Microsoft 365 application URLs within the `*.cloud.microsoft` domain. Allow the entire domain to help maintain service reliability.

If your organization blocks `copilot.cloud.microsoft` to prevent personal Microsoft account sign-in, consider using [tenant restrictions](https://learn.microsoft.com/en-us/entra/external-id/tenant-restrictions-v2#step-2-block-consumer-account-or-microsoft-account-tenants) as a targeted control.

For more information, see [Unified cloud.microsoft domain for Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain).

### WebSockets requirements

Verify full WebSocket Secure \(WSS\) connectivity from user devices running Microsoft 365 applications to these domains:

- `*.office.com`
- `*.cloud.microsoft`
- `copilot.cloud.microsoft`

Copilot integrations can fail when a network perimeter blocks WSS, a network device performs Transport Layer Security inspection that interferes with the connection, or a proxy enforces aggressive connection timeouts.

Work with the teams that manage network security, proxies, firewalls, secure web gateways, or SSE/SASE services to allow the required traffic. You can test connectivity to the `*.cloud.microsoft` domain by using either the [connectivity test for the Copilot app](https://connectivity.m365.cloud.microsoft/copilot). You can also use the [Microsoft 365 connectivity test tool](https://connectivity.m365.cloud.microsoft) for broader Microsoft products and service.

### Wildcards, FQDNs, and subdomains

Where Microsoft 365 network guidance specifies a wildcard, allow the wildcard and its required subdomains. Microsoft 365 services are dynamic and don't provide a fixed list of individual fully qualified domain names for every Copilot feature and scenario.

## Secure and governed foundation

Although not required, it's strongly recommended to [configure a secure and governed foundation for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-secure-governed-data-foundation-microsoft-365-copilot). When your organization's data is well governed, current, and appropriately shared, Copilot can deliver accurate, relevant, and secure responses. By using SharePoint Advanced Management and Microsoft Purview capabilities, you can:

- Remediate oversharing
- Set up guardrails to protect data by default
- Meet AI regulations and regulatory requirements

The following table summarizes capabilities you can configure. Also see [Secure and govern Microsoft Copilot: Foundational deployment guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance).

| Product | Description |
| --- | --- |
| [SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management) | SharePoint Advanced Management is a set of configurable capabilities that provides administrative content governance controls for SharePoint and OneDrive. SharePoint Advanced Management is available as part of Microsoft 365 Copilot or as an add-on.  <br>  <br>See the following articles:  <br>- [What is SharePoint Advanced Management?](https://learn.microsoft.com/en-us/sharepoint/advanced-management)  <br>- [Get ready for Microsoft Copilot and agents with SharePoint Advanced Management](https://learn.microsoft.com/en-us/microsoft-365/copilot/get-ready-copilot-sharepoint-advanced-management) |
| [Microsoft Purview](https://learn.microsoft.com/en-us/purview/purview) | Microsoft Purview helps to mitigate and manage the risks associated with AI usage, and implement corresponding protection and governance controls.  <br>  <br>See the following articles:  <br>- [Use Microsoft Purview to manage data security & compliance for Microsoft Copilot & Microsoft Copilot Chat](https://learn.microsoft.com/en-us/purview/ai-m365-copilot)  <br>- [Enable sensitivity labels for files in SharePoint and OneDrive](https://learn.microsoft.com/en-us/purview/sensitivity-labels-sharepoint-onedrive-files) |

## Web search requirements

Web search is a configurable Copilot capability. When web search is allowed and information from the web can improve a response, Copilot can retrieve information from the Bing search service.

Admins can manage web search by using the applicable Copilot policy. For more information, see [Manage web search in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access).

## Validate a user's configuration

Use the [Copilot License Details diagnostic](https://aka.ms/CopilotLicenseDetails) to check whether a user account meets applicable licensing requirements for Copilot features.

## Related content

- [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview)
- [License options for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing)
- [Add Microsoft Copilot endpoints to your allow list](https://learn.microsoft.com/en-us/microsoft-365/copilot/add-copilot-endpoints-allowlist)
