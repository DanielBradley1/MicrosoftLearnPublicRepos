<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/office-365-ti -->
<!-- Sitemap-Last-Modified: 2025-05-21 -->

# Threat investigation and response

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

Threat investigation and response capabilities in [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) help security analysts and administrators protect their organization's Microsoft 365 for business users by:

- Making it easy to identify, monitor, and understand cyberattacks.
- Helping to quickly address threats in Exchange Online, SharePoint, OneDrive and Microsoft Teams.
- Providing insights and knowledge to help security operations prevent cyberattacks against their organization.
- Employing [automated investigation and response in Office 365](https://learn.microsoft.com/en-us/defender-office-365/air-about) for critical email-based threats.

Threat investigation and response capabilities provide insights into threats and related response actions that are available in the Microsoft Defender portal. These insights can help your organization's security team protect users from email- or file-based attacks. The capabilities help monitor signals and gather data from multiple sources, such as user activity, authentication, email, compromised PCs, and security incidents. Business decision makers and your security operations team can use this information to understand and respond to threats against your organization and protect your intellectual property.

## Get acquainted with threat investigation and response tools

Threat investigation and response capabilities in the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com) are a set of tools and response workflows that include:

- [Explorer](#explorer)
- [Incidents](#incidents)
- [Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations)
- [Automated investigation and response](https://learn.microsoft.com/en-us/defender-office-365/air-about)

### Explorer

Use [Explorer \(and real-time detections\)](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about) to analyze threats, see the volume of attacks over time, and analyze data by threat families, attacker infrastructure, and more. Explorer \(also referred to as Threat Explorer\) is the starting place for any security analyst's investigation workflow.

[![The Threat explorer page](https://learn.microsoft.com/en-us/defender-office-365/media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png)](https://learn.microsoft.com/en-us/defender-office-365/media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png#lightbox)

To view and use this report in the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Explorer**. Or, to go directly to the **Explorer** page, use [https://security.microsoft.com/threatexplorer](https://security.microsoft.com/threatexplorer).

#### Office 365 Threat Intelligence connection

This feature is only available if you have an active Office 365 E5 or G5 or Microsoft 365 E5 or G5 subscription or the Threat Intelligence add-on. For more information, see the Office 365 Enterprise E5 product page.

Data from Microsoft Defender for Office 365 is incorporated into Microsoft Defender to conduct a comprehensive security investigation in Office 365 mailboxes and Windows devices.

### Incidents

Use the Incidents list \(this is also called Investigations\) to see a list of in flight security incidents. Incidents are used to track threats such as suspicious email messages, and to conduct further investigation and remediation.

[![The list of current Threat Incidents in Office 365](https://learn.microsoft.com/en-us/defender-office-365/media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png)](https://learn.microsoft.com/en-us/defender-office-365/media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png#lightbox)

To view the list of current incidents for your organization in the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Incidents & alerts** > **Incidents**. Or, to go directly to the **Incidents** page, use [https://security.microsoft.com/incidents](https://security.microsoft.com/incidents).

### Attack simulation training

Use Attack simulation training to set up and run realistic cyberattacks in your organization, and identify vulnerable people before a real cyberattack affects your business. To learn more, see [Simulate a phishing attack](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations).

To view and use this feature in the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Attack simulation training**. Or, to go directly to the **Attack simulation training** page, use [https://security.microsoft.com/attacksimulator?viewid=overview](https://security.microsoft.com/attacksimulator?viewid=overview).

### Automated investigation and response

Use automated investigation and response \(AIR\) capabilities to save time and effort correlating content, devices, and people at risk from threats in your organization. AIR processes can begin whenever certain alerts are triggered, or when started by your security operations team. To learn more, see [Automated investigation and response \(AIR\) examples in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/air-examples).

## Threat intelligence widgets

As part of the Microsoft Defender for Office 365 Plan 2 offering, security analysts can review details about a known threat. This is useful to determine whether there are additional preventative measures/steps that can be taken to keep users safe.

[![The Security trends pane showing information about recent threats](https://learn.microsoft.com/en-us/defender-office-365/media/11e7d40d-139b-4c56-8d52-c091c8654151.png)](https://learn.microsoft.com/en-us/defender-office-365/media/11e7d40d-139b-4c56-8d52-c091c8654151.png#lightbox)

## How do we get these capabilities?

Microsoft 365 threat investigation and response capabilities are included in Microsoft Defender for Office 365 Plan 2, which is included in Enterprise E5 or as an add-on to certain subscriptions. To learn more, see [Defender for Office 365 Plan 1 vs. Plan 2 cheat sheet](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

## Required roles and permissions

Microsoft Defender for Office 365 uses role-based access control. Permissions are assigned through certain roles in Microsoft Entra ID, the Microsoft 365 admin center, or the Microsoft Defender portal.

Tip

Although some roles, such as Security Administrator, can be assigned in the Microsoft Defender portal, consider using either the Microsoft 365 admin center or Microsoft Entra ID instead. For information about roles, role groups, and permissions, see the following resources:

- [Permissions in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions)
- [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference)
- [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac)

| Activity | Roles and permissions |
| --- | --- |
| Use the Microsoft Defender Vulnerability Management dashboard  <br>  <br>View information about recent or current threats | One of the following:<br><br>- **Global Administrator**<sup>\*</sup><br>- **Security Administrator**<br>- **Security Reader**<br><br>  <br>These roles can be assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\). |
| Use [Explorer \(and real-time detections\)](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about) to analyze threats | One of the following:<br><br>- **Global Administrator**<sup>\*</sup><br>- **Security Administrator**<br>- **Security Reader**<br><br>  <br>These roles can be assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\). |
| View Incidents \(also referred to as Investigations\)  <br>  <br>Add email messages to an incident | One of the following:<br><br>- **Global Administrator**<sup>\*</sup><br>- **Security Administrator**<br>- **Security Reader**<br><br>  <br>These roles can be assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\). |
| Trigger email actions in an incident  <br>  <br>Find and delete suspicious email messages | One of the following:<br><br>- **Global Administrator**<sup>\*</sup><br>- **Security Administrator** plus the **Search and Purge** role<br><br>  <br>The **Global Administrator**<sup>\*</sup> and **Security Administrator** roles can be assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\).  <br>  <br>The **Search and Purge** role must be assigned in the **Email & collaboration roles** in the Microsoft 365 Defender portal \([https://security.microsoft.com](https://security.microsoft.com)\). |
| Integrate Microsoft Defender for Office 365 Plan 2 with Microsoft Defender for Endpoint  <br>  <br>Integrate Microsoft Defender for Office 365 Plan 2 with a SIEM server | Either the **Global Administrator**<sup>\*</sup> or the **Security Administrator** role assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\).  <br>  <br>--- **plus** ---  <br>  <br>An appropriate role assigned in additional applications \(such as [Microsoft Defender Security Center](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/user-roles) or your SIEM server\). |
| View email preview/download .eml of Quarantined emails \(view/download only Quarantined emails\) | One of the following:<br><br>- **Global Administrator**<sup>\*</sup><br>- **Security Administrator**<br>- **Security Reader**<br><br>  <br>These roles can be assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\). |
| View email preview/download .eml of ANY email in Explorer | One of the following:<br><br>- **Security Administrator**<br>- **Security Reader**<br><br>  <br>These roles can be assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\). |

Important

<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

## Next steps

- [Threat trackers in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/threat-trackers)
- [Find and investigate malicious email that was delivered \(Office 365 Threat Investigation and Response\)](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-investigate-delivered-malicious-email)
- [Simulate a phishing attack](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations)
