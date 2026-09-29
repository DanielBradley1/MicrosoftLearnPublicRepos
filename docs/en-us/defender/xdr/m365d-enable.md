<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-enable -->
<!-- Sitemap-Last-Modified: 2024-08-12 -->

# Turn on Microsoft Defender XDR

**Applies to:**

- Microsoft Defender XDR

[Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender) unifies your incident response process by integrating key capabilities across Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps, and Microsoft Defender for Identity. This unified experience adds powerful features you can access in the Microsoft Defender portal.

Microsoft Defender XDR automatically turns on when eligible customers with the required permissions visit Microsoft Defender portal. Read this article to understand various prerequisites and how Microsoft Defender XDR is provisioned.

## Check license eligibility and required permissions

A license to a Microsoft 365 security product generally entitles you to use Microsoft Defender XDR without additional licensing cost. We do recommend getting a Microsoft 365 E5, E5 Security, A5, or A5 Security license or a valid combination of licenses that provides access to all supported services.

For detailed licensing information, [read the licensing requirements](https://learn.microsoft.com/en-us/defender-xdr/prerequisites#licensing-requirements).

### Check your role

You must be one of the following roles to turn on Microsoft Defender XDR:

- Global Administrator
- Security Administrator
- Security Operator
- Global Reader
- Security Reader
- Compliance Administrator
- Compliance Data Administrator
- Application Administrator
- Cloud Application Administrator

[View your roles in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## Configure your network firewall

Configuring your network firewall ensures a smooth experience while navigating the Microsoft Defender portal [https://security.microsoft.com](https://security.microsoft.com).

Add to your firewall's allow list the outbound IP addresses in the following page:

- [IP addresses used by Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/ip-addresses#outgoing-ports)

In addition, ensure that other Defender services are properly configured. You can refer to the following pages for configuration information:

- [Enable access to Microsoft Defender for Endpoint service in the proxy server](https://learn.microsoft.com/en-us/defender-endpoint/configure-environment#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)
- [Get started with Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-deployment-guide)
- [Configure endpoint proxy and internet connectivity settings for Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-proxy)
- [Ensure portal access for Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/network-requirements#portal-access)

## Supported services

Microsoft Defender XDR aggregates data from the various supported services that you've already deployed. It will process and store data centrally to identify new insights and make centralized response workflows possible. It does this without affecting existing deployments, settings, or data associated with the integrated services.

To get the best protection and optimize Microsoft Defender XDR, we recommend deploying all applicable supported services on your network. For more information, [read about deploying supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

## Onboard to the service

Onboarding to Microsoft Defender XDR is simple. From the navigation menu, select any item, such as **Incidents & alerts**, **Hunting**, **Action center**, or **Threat analytics** to initiate the onboarding process.

### Data center location

Microsoft Defender XDR will store and process data in the [same location used by Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). If you don't have Microsoft Defender for Endpoint, a new data center location is automatically selected based on the location of active Microsoft 365 security services. The selected data center location is shown in the screen.

Select **Need help?** in the Microsoft Defender portal to contact Microsoft support about provisioning Microsoft Defender XDR in a different data center location.

Note

In the past, Microsoft Defender for Endpoint automatically provisioned in European Union \(EU\) data centers when turned on through Microsoft Defender for Cloud. Microsoft Defender XDR will automatically provision in the same EU data center for customers who have provisioned Defender for Endpoint in this manner in the past.

### Confirm that the service is on

Once the service is provisioned, it adds:

- [Incidents management](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview)
- [Alerts queue](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts)
- An action center for managing [automated investigation and response](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir)
- [Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) capabilities
- Threat analytics

[![The navigation pane in the Microsoft Defender portal with Microsoft Defender XDR features](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-enable/overview-incident.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-enable/overview-incident.png#lightbox) *Microsoft Defender portal with incidents management and other capabilities*

### Getting Microsoft Defender for Identity data

To enable the integration with Microsoft Defender for Cloud Apps, you'll need to log in to the Microsoft Defender for Cloud Apps at least once.

## Get assistance

To get answers to the most commonly asked questions about turning on Microsoft Defender XDR, [read the FAQ](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable-faq).

Microsoft support staff can help provision or deprovision the service and related resources on your tenant. For assistance, select **Need help?** in the Microsoft Defender portal. When contacting support, mention Microsoft Defender XDR.

## Related topics

- [Frequently asked questions](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable-faq)
- [Licensing requirements and other prerequisites](https://learn.microsoft.com/en-us/defender-xdr/prerequisites)
- [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services)
- [Setup guides for Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/deploy-configure-m365-defender)
- [Microsoft Defender XDR overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Microsoft Defender for Endpoint overview](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Defender for Office 365 overview](https://learn.microsoft.com/en-us/defender-office-365/mdo-about)
- [Microsoft Defender for Cloud Apps overview](https://learn.microsoft.com/en-us/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Defender for Identity overview](https://learn.microsoft.com/en-us/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender for Endpoint data storage](https://learn.microsoft.com/en-us/defender-endpoint/data-storage-privacy)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
