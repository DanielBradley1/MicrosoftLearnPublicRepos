<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-enable-faq -->
<!-- Sitemap-Last-Modified: 2025-01-20 -->

# Microsoft Defender XDR frequently asked questions

Read responses to the most commonly asked questions about [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender), including required licenses and permissions, deploying support services, initial settings, and feedback.

For instructions on how to turn on the service, [read Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable).

## I don't have a Microsoft 365 E5 license. Can I still use Microsoft Defender XDR?

Customers with the following non-E5 licenses can use Microsoft Defender XDR:

- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Defender for Office 365 \(Plan 2\)

For a full list of supported licenses, [read the licensing requirements](https://learn.microsoft.com/en-us/defender-xdr/prerequisites#licensing-requirements).

## Do I need to install or deploy anything to start using Microsoft Defender XDR?

No, Microsoft Defender XDR consolidates data from Microsoft 365 security services that you have already deployed. Once you turn it on, incident, automation, and hunting experiences will start working within the scope of the deployed products. If none of these products are properly deployed, Microsoft Defender XDR will not display any data and is unable to take any action.

To optimize your Microsoft Defender XDR experiences, we recommend deploying *all* supported [Microsoft 365 security products and services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

## Where does Microsoft Defender XDR process and store my data?

Microsoft Defender XDR automatically selects an optimal location for the data center where consolidated data is processed and stored. If you have Microsoft Defender for Endpoint, it selects the same location used by Defender for Endpoint.

Note

Microsoft Defender for Endpoint automatically provisions in European Union \(EU\) data centers when turned on through Microsoft Defender for Cloud. Microsoft Defender XDR will automatically provision in the same EU data center for customers who have provisioned Microsoft Defender for Endpoint in this manner.

The data center location is shown before and after the service is provisioned in the settings page for Microsoft Defender XDR \(**Settings > Microsoft Defender XDR**\). If you prefer to use another data center location, select **Need help?** in the Microsoft Defender portal to contact Microsoft support.

## Where can I access Microsoft Defender XDR?

Microsoft Defender XDR is available at: [https://security.microsoft.com](https://security.microsoft.com).

## What permissions do I need to access Microsoft Defender XDR?

Accounts assigned the following Microsoft Entra roles can access Microsoft Defender XDR functionality and data:

- [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)
- [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator)
- [Security Operator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-operator)
- [Global Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader)
- [Security Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader)
- [Compliance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#compliance-administrator)
- [Compliance Data Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#compliance-data-administrator)
- [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
- [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)

Note

Role-based access control settings in Microsoft Defender for Endpoint influence access to data. For more information, read about [managing access to Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions).

If you are running the Microsoft Defender XDR preview program you can now also experience the new Microsoft Defender 365 role-based access control \(RBAC\) model. For more information, see [Microsoft Defender XDR role-based access control \(RBAC\) model](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## What time zone does Microsoft Defender XDR default to?

By default, Microsoft Defender XDR displays time information in the UTC time zone. You can also change this setting to use your local time zone.

To change time zone, sign in to the Microsoft Defender portal then go to **System > Settings > Microsoft Defender portal** and select your preferred time zone. Refresh your browser to ensure that changes are applied immediately.

The time zone settings is applied to the dates and times displayed in incidents, automated investigation and remediation, and advanced hunting.

## How can I learn about new Microsoft Defender XDR feature and UI updates?

Microsoft regularly provides information through the various channels, including:

- Blog posts in the [Microsoft Defender XDR Blog](https://techcommunity.microsoft.com/category/microsoft-defender-xdr/blog/microsoftthreatprotectionblog)
- Go to [Defender monthly news](https://aka.ms/defendernews)
- The [message center](https://learn.microsoft.com/en-us/Microsoft-365/admin/manage/message-center) in Microsoft 365 admin center

Get the latest publicly available experiences by turning on [preview features](https://learn.microsoft.com/en-us/defender-xdr/preview).

## How can I provide feedback or suggestions for Microsoft Defender XDR?

Your feedback helps us get better at protecting your environment from advanced attacks. Share your experience, impressions, and requests by providing feedback.

In the Microsoft Defender portal, select the feedback icon on the top right and provide your feedback.

![Screenshot of the portal menu, highlighting the feedback icon](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-enable-faq/portal-feedback.png)

Rate your experience and provide details on what you liked or where improvements can be made. You can also choose to be contacted about the feedback.

## Related topics

- [Microsoft Defender XDR overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable).
- [Licensing requirements and other prerequisites](https://learn.microsoft.com/en-us/defender-xdr/prerequisites)
- [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services)
- [Setup guides for Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/deploy-configure-m365-defender)
- [Turn on preview features](https://learn.microsoft.com/en-us/defender-xdr/preview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
