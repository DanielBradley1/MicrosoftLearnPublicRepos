<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-requirements -->
<!-- Sitemap-Last-Modified: 2026-09-24 -->

# Microsoft 365 app and network requirements for Microsoft Copilot

Important

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. The primary URL for accessing the updated Copilot app will be `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [Recommended actions](#recommended-actions) \(in this article\).

[Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview) is an AI-powered productivity tool that integrates with Microsoft 365 Apps. This integration allows users to use Copilot in individual apps, such as Word, PowerPoint, Teams, Excel, Outlook, and more. The Copilot experiences are designed to provide users with an AI assistant in the apps they use every day.

As a result of this integration, there are some app and network requirements for Microsoft Copilot to integrate with your Microsoft 365 apps. These requirements are nearly identical to the requirements for using Microsoft 365 Apps.

As part of your [Microsoft Copilot adoption](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-enablement-resources), make sure you configure the app and network requirements that allow the app integration.

[![Screenshot of the app and network requirements step to adopt and enable Microsoft Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-enablement-resources/adopt-copilot-apps-privacy-network.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-enablement-resources/adopt-copilot-apps-privacy-network.png#lightbox)

This article lists the Microsoft 365 app and network requirements to use Microsoft Copilot in your Microsoft 365 apps.

This article applies to:

- Microsoft Copilot

## Prerequisites

- Users must have a Microsoft 365 license assigned to them. You can find the list of eligible base licenses in [Microsoft Copilot license options](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing) or in the [Microsoft 365 Copilot service description guide](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-copilot).
- Users must have [Microsoft Entra ID](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/add-users) accounts. You can add or sync users by using the [onboarding wizard in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=m365setup#/modernonboarding/identitywizard).
- Microsoft Copilot supports primary mailboxes that are hosted on Exchange Online. It's also available on users' archive mailboxes and shared and delegate mailboxes that they have access to.

Note

Chat experiences in Word, Excel, and PowerPoint vary depending on your tenant configuration and license. Learn more in [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview#copilot-features-in-microsoft-365-apps). To enable users with priority access to these capabilities, learn more about [Microsoft Copilot](https://www.microsoft.com/microsoft-365/microsoft-365-enterprise).

## App requirements

- **[Microsoft 365 Apps](https://learn.microsoft.com/en-us/deployoffice/about-microsoft-365-apps)** - You must deploy the apps. Use the [Microsoft 365 Apps setup guide in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=learndocs#/modernonboarding/microsoft365copilotsetupguide) to deploy the apps to your users.

  Note

  - For Copilot to work in Word Online, Excel Online, and PowerPoint Online, you must enable third-party cookies.
  - Review your privacy settings for Microsoft 365 Apps. These settings might affect the availability of Microsoft Copilot features. For more information, see [Microsoft Copilot and privacy controls for connected experiences](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#microsoft-copilot-and-privacy-controls-for-connected-experiences).
  - Copilot isn't available when using device-based licensing for Microsoft 365 Apps for enterprise.

- **Microsoft OneDrive** - Some features in Microsoft Copilot, such as file restore and OneDrive management, require that users have a [OneDrive account](https://learn.microsoft.com/en-us/sharepoint/introduction). Use the [OneDrive setup guide in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=m365setup#/modernonboarding/onedrivequickstartguide) to enable OneDrive for your users.
- **Microsoft Outlook** - Microsoft Copilot works with classic Outlook and new Outlook \(for [Windows](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627) and [Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)\). Users can switch to the new Outlook by selecting **Try the new Outlook** in their existing Outlook client.

  Important

  Microsoft Copilot isn't available on group mailboxes.
- **Microsoft Teams** - Use the [Microsoft Teams setup guide in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=m365setup#/modernonboarding/microsoftteamssetupguide) to configure popular Teams settings, including external access, guest access, team creation permissions, and more. Copilot in Teams is available on Windows, Mac, web, Android, and iOS.

  To enable Copilot in Teams to reference meeting content after the meeting ends, enable transcription or meeting recording. To learn more about configuring transcription and recording, see [Configure transcription and captions for Teams meetings](https://learn.microsoft.com/en-us/microsoftteams/meeting-transcription-captions) and [Teams meeting recording](https://learn.microsoft.com/en-us/microsoftteams/meeting-recording).
- **Microsoft Teams Phone** - Copilot in [Teams Phone](https://learn.microsoft.com/en-us/microsoftteams/what-is-phone-system-in-office-365) supports voice over Internet Protocol \(VOIP\) and public switched telephone network \(PSTN\) calls.

  - For support across VoIP calls, you need a Microsoft Copilot license.
  - To use Copilot for PSTN calls, you need a Teams Phone license, a calling plan, and a Microsoft Copilot license.
  - To enable Copilot in Teams Phone, you need to turn on transcription or recording.


  For VoIP callers, all participants see a notification that the call is being transcribed or recorded. For PSTN callers, all participants hear an announcement that the call is being recorded.

- **Microsoft Loop** - To use Microsoft Copilot with Microsoft Loop, you must have Loop enabled for your tenant. Enable Loop in the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home#/Settings/Services/:/Settings/L1/Loop) or the [Microsoft 365 Apps admin center](https://config.office.com) under **Customization** \| **Policy Management**. To learn more, see:

  - [Manage Loop workspaces in Syntex repository services](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-workspaces-configuration)
  - [Learn how to enable the Microsoft Loop app](https://techcommunity.microsoft.com/t5/microsoft-365-blog/learn-how-to-enable-the-microsoft-loop-app-now-in-public-preview/ba-p/3769013).

- **Microsoft Whiteboard** - To use Microsoft Copilot with Microsoft Whiteboard, you must have Whiteboard enabled for your tenant. To learn more about Microsoft Whiteboard, see [Manage access to Microsoft Whiteboard for your organization](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-whiteboard-access-organizations).

## Review app privacy

Review your Microsoft 365 apps privacy settings. The privacy settings in your Microsoft 365 apps can affect the availability of Microsoft Copilot features. To ensure that users can access Copilot features, review the privacy settings in your Microsoft 365 apps.

To learn more, see [Microsoft Copilot and privacy controls for connected experiences](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#microsoft-copilot-and-privacy-controls-for-connected-experiences).

## Run the Office Feature Updates task

The Office Feature Updates task is required for core Copilot experiences in apps such as Word, PowerPoint, Excel, and OneNote, to work properly. This task should run on its regular schedule and access the required network resources.

For more information about the Office Feature Updates task, see [Office Feature Updates task description and FAQ](https://learn.microsoft.com/en-us/microsoft-365/troubleshoot/updates/office-feature-updates-task-faq).

For more information about the network resources to allow, see [Network requirements](#network-requirements) \(in this article\).

## Network requirements

Configure your network for Microsoft Copilot. Copilot experiences are deeply integrated with Microsoft 365 applications and often use the same [network connections and endpoints that Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges) use.

Baseline network configuration customers should:

- Ensure that their environment doesn't block the Microsoft 365 endpoints listed in the section, [Network endpoint requirements](#network-endpoint-requirements).
- Verify that their network setup follows [Microsoft 365 network connectivity principles and best practices](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles).

To help ensure users' connections aren't blocked, take these steps:

- Add `*.cloud.microsoft` to your organization's allow lists on devices and your network infrastructure.
- Verify that rules, category filters, Conditional Access, or app control policies aren't blocking `copilot.cloud.microsoft` or the Copilot app.
- Confirm that your environment aligns to [recommended network configurations for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-requirements#network-requirements).

You might need to work with the teams managing your network, proxy, and firewalls, or your network service/SASE/SSE provider to ensure that traffic to `*.cloud.microsoft` isn't blocked or otherwise interfered with.

You can test connectivity to endpoints in the `*.cloud.microsoft` domain by using the [Microsoft 365 Connectivity test tool](https://connectivity.office.com/).

For more information, see [Unified cloud.microsoft domain for Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain).

### Network endpoint requirements

- Allow the [worldwide Microsoft 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).
- Add the [Microsoft Copilot endpoints to your allow list](https://learn.microsoft.com/en-us/microsoft-365/copilot/add-copilot-endpoints-allowlist).

For more information about the Microsoft Copilot app, see [Microsoft Copilot app overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-overview).

### WebSockets \(WSS\) protocol requirements

Verify that your network supports full WSS connectivity from user devices running Microsoft 365 applications to the following domains:

- Microsoft Copilot enterprise experiences: `*.office.com`, `*.cloud.microsoft` and `copilot.cloud.microsoft`.

Several Copilot integrations rely on WebSockets \(WSS\) to deliver a streamlined user experience. Some customer networks might not be configured to handle WSS connections properly, which can result in Copilot application failures. Typical network configurations that affect WSS include:

- The network perimeter blocks the WSS protocol
- Network devices attempting to perform Transport Layer Security \(TLS\) inspection of connections
- Proxy servers enforcing aggressive connection timeouts

#### Recommended actions

- Ensure that `copilot.cloud.microsoft` isn't blocked within your environment. Check for legacy filtering rules, URL category restrictions, proxy policies, firewall rules, tenant restrictions, Conditional Access policies, or app control policies that might block `copilot.cloud.microsoft`.
- Add `*.cloud.microsoft` to your organization's allow lists. For tenant-specific network configurations and allow list requirements, contact your Microsoft support team for guidance. Microsoft doesn't support allowing partial or only selected Microsoft 365 application URLs within the `*.cloud.microsoft` domain. Allow the entire `*.cloud.microsoft` domain to maintain service reliability and avoid disruptions.
- Coordinate with teams that manage network security, proxy services, firewalls, secure web gateways, SSE/SASE platforms, or third-party filtering solutions to ensure traffic to `*.cloud.microsoft` is permitted.
- If preventing personal Microsoft account sign-ins is the reason your organization blocks `copilot.cloud.microsoft`, consider using [Tenant Restrictions](https://learn.microsoft.com/en-us/entra/external-id/tenant-restrictions-v2#step-2-block-consumer-account-or-microsoft-account-tenants) as the targeted control. The control allows your organization to permit access to the Copilot service URL while restricting authentication with personal Microsoft accounts on managed networks or devices.
- You can validate connectivity to the `*.cloud.microsoft` domain by using the [Microsoft 365 Connectivity Test tool](https://connectivity.office.com/).

For more information, see [Unified cloud.microsoft domain for Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain).

### FQDNs and subdomains

Some organization might prefer to use granular definitions of endpoints, like individual FQDNs, instead of wildcards to configure their network settings. Due to hyperscale and the dynamic nature of its services, Microsoft 365 can't provide specific FQDNs used by individual features and scenarios. Doing so would result in unmanageable configuration surface, constant customer network changes, and connectivity incidents.

When you review and implement the recommended network configurations, consider all the FQDNs and subdomains where wildcards are specified. These wildcards include functionality that the referenced scenarios require.

## Related content

- [Microsoft Copilot app overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-overview)
- [Microsoft Copilot setup guide in the Microsoft admin center](https://admin.microsoft.com/Adminportal/Home?Q=learndocs#/modernonboarding/microsoft365copilotsetupguide)
- [Copilot Prompt Gallery](https://m365.cloud.microsoft/copilot-prompts)
- [Microsoft Copilot - Microsoft Community Hub](https://techcommunity.microsoft.com/t5/microsoft-365-copilot/ct-p/Microsoft365Copilot)
- [Microsoft Copilot adoption guide and overview for IT admins](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-reports-for-admins)
