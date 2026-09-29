<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/mdo-about -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Microsoft Defender for Office 365 overview

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

Although all organizations with cloud mailboxes include [built-in security features](https://learn.microsoft.com/en-us/defender-office-365/eop-about), Microsoft Defender for Office 365 is the primary email and collaboration security solution for Microsoft 365.

This article explains the *protection ladder* for email and collaboration. The ladder starts with the built-in security features for all cloud mailboxes, and continues to Defender for Office 365 Plan 1 and Defender for Office 365 Plan 2.

Tip

As a companion to this article, see our [Microsoft Defender for Office 365 setup guide](https://setup.cloud.microsoft/defender/office-365-setup-guide) to review best practices and to protect against email, link, and collaboration threats. Features include Safe Links, Safe Attachments, and more. For a customized experience based on your environment, you can access the [Microsoft Defender for Office 365 automated setup guide](https://admin.microsoft.com/Adminportal/Home?Q=ADG#/modernonboarding/office365advancedthreatprotectionadvisor) in the Microsoft 365 admin center.

This article is intended for Security Operations \(SecOps\) personnel, Microsoft 365 admins, or decision makers who want to learn more about Defender for Office 365.

Tip

If you're using **Outlook.com**, **Microsoft 365 Family**, or **Microsoft 365 Personal**, and need information about *Safelinks* or *advanced attachment scanning*, see [Advanced Outlook.com security for Microsoft 365 subscribers](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

If you're new to your Microsoft 365 subscription and would like to know your licenses before you begin, go to the **Your products** page in the Microsoft 365 admin center at [https://admin.microsoft.com/Adminportal/Home#/subscriptions](https://admin.microsoft.com/Adminportal/Home#/subscriptions).

The protection ladder in Defender for Office 365 contains the following elements:

1. **The built-in security features for all cloud mailboxes**: Included in all Microsoft 365 subscriptions with cloud mailboxes.
2. **Defender for Office 365 Plan 1**: Included in some Microsoft 365 subscriptions that cater to small to medium-sized businesses \(for example, Microsoft 365 E3/G3 and Microsoft 365 Business Premium\).
3. **Defender for Office 365 Plan 2**: Included in some Microsoft 365 subscriptions that cater to enterprise organizations \(for example, Microsoft 365 A5/E5/G5\).

Defender for Office 365 is also available as an add-on subscription to many Microsoft 365 subscriptions with cloud mailboxes.

Defender for Office 365 Plan 1 contains a subset of the features that are available in Plan 2. Defender for Office 365 Plan 2 contains many features that aren't available in Plan 1.

Tip

For information about subscriptions that contain Defender for Office 365, see the [Microsoft 365 business plan comparison](https://aka.ms/M365BusinessPlans) and the [Microsoft 365 Enterprise plan comparison](https://aka.ms/M365EnterprisePlans).

Use the following exhaustive reference to determine if Defender for Office 365 Plan 1 or Plan 2 licenses are included in a Microsoft 365 subscription: [Product names and service plan identifiers for licensing](https://learn.microsoft.com/en-us/entra/identity/users/licensing-service-plan-reference).

Use the following interactive guide to see how Defender for Office 365 is able to protect your organization: [Safeguard your organization with Microsoft Defender for Office 365](https://aka.ms/MSDO-IG).

Use [this page](https://www.microsoft.com/security/business/siem-and-xdr/microsoft-defender-office-365#pmg-allup-content) to compare plans and purchase Defender for Office 365.

The following descriptions summarize the protection ladder in Defender for Office 365:

- **The built-in security features for all cloud mailboxes** prevent broad, volume-based, known email attacks.
- **Defender for Office 365 Plan 1** protects email and collaboration features from zero-day malware, phishing, and business email compromise \(BEC\).
- **Defender for Office 365 Plan 2** adds phishing simulations, post-breach investigation, hunting, and response, and automation.

However, you can also think about the *architecture* of protection in Defender for Office 365 as *cumulative layers of security*, where each layer has a different *security emphasis*. This architecture is shown in the following diagram:

[![Diagram about protections in Defender for Office 365 and their relationships to one another with service emphasis, including a note for email authentication.](https://learn.microsoft.com/en-us/defender-office-365/media/eop-mdop1-mdop2-comparison.png)](https://learn.microsoft.com/en-us/defender-office-365/media/eop-mdop1-mdop2-comparison.png#lightbox)

All levels of the protection ladder are capable of protecting, detecting, investigating, and responding to threats. But as you move up the protection ladder, the *available features* and *automation* increase.

Whether you're using the onmicrosoft.com domain only or custom domains for email in Microsoft 365, it's important to configure email authentication for your used and unused domains. SPF, DKIM, and DMARC records in DNS allow Microsoft 365 to more accurately protect against spoofing attacks. For more information, see [Email authentication](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-about).

## The Defender for Office 365 security ladder

It can be difficult to identify the advantages of Defender for Office 365. The following subsections describe the capabilities of each product using the following security emphases:

- Preventing and detecting threats.
- Investigating threats.
- Responding to threats.

### Capabilities of the built-in security features for all cloud mailboxes

The built-in security features included in all organizations with cloud mailboxes are summarized in the following table:

| Prevent/Detect | Investigate | Respond |
| --- | --- | --- |
| - [Anti-malware protection](https://learn.microsoft.com/en-us/defender-office-365/anti-malware-protection-about)<sup>\*</sup><br>- [Anti-spam protection](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-protection-about)<sup>\*</sup>, including [bulk email protection](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-spam-vs-bulk-about)<br>- [Anti-phishing \(spoofing\) protection](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-protection-spoofing-about)<sup>\*</sup>, including the [Spoof intelligence insight](https://learn.microsoft.com/en-us/defender-office-365/anti-spoofing-spoof-intelligence)<br>- [Outbound spam protection](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-protection-about)<br>- [Connection filtering](https://learn.microsoft.com/en-us/defender-office-365/connection-filter-policies-configure)<br>- [Quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-about) and [quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies)<br>- False positives and false negative reporting by [admin submissions to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin) and [user reported messages](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox)<br>- [Allow and block entries in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about) for:<br><br>  - Domains and email addresses<br>  - Spoof<br>  - URLs<br>  - Files | - [Audit log search](https://learn.microsoft.com/en-us/defender-office-365/audit-log-search-defender-portal)<br>- [Message Trace](https://learn.microsoft.com/en-us/defender-office-365/message-trace-defender-portal)<br>- [Email security reports](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security) | - [Zero-hour auto purge \(ZAP\) for email](https://learn.microsoft.com/en-us/defender-office-365/zero-hour-auto-purge#zero-hour-auto-purge-zap-for-email-messages)<br>- Refine and test entries in the [Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about) |

<sup>\*</sup> The associated features are available in default threat policies, custom threat policies, and [the Standard and Strict preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies). For help with deciding which method to use, see [Determine your threat policy strategy](https://learn.microsoft.com/en-us/defender-office-365/mdo-deployment-guide#determine-your-protection-policy-strategy).

For more information, see [Built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about).

### Defender for Office 365 Plan 1 capabilities

Defender for Office 365 Plan 1 adds more *prevention* and *detection* capabilities.

The extra features you get in **Defender for Office 365 Plan 1** on top of the built-in security features for all cloud mailboxes are described in the following table:

| Prevent/Detect | Investigate | Respond |
| --- | --- | --- |
| - The following [extra features in anti-phishing policies](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-protection-about#additional-anti-phishing-protection-in-microsoft-defender-for-office-365), including the [impersonation insight](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-mdo-impersonation-insight):<br><br>  - User and domain impersonation protection<br>  - Mailbox intelligence impersonation protection \(contact graph\)<br>  - [Phishing email thresholds](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-about#phishing-email-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)<br><br>- [Safe Attachments in email](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-about)<br>- [Safe Attachments for files in SharePoint, OneDrive, and Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-for-spo-odfb-teams-about)<br>- [Safe Links in email, Office clients, and Teams](https://learn.microsoft.com/en-us/defender-office-365/safe-links-about)<br>- Email & collaboration alerts at [https://security.microsoft.com/viewalertsv2](https://security.microsoft.com/viewalertsv2)<br>- Security information and event management \(SIEM\) integration from Office 365 Management APIs for **alerts**. For more information, see [Security and Compliance Alerts schema](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema).<br>- [Tenant Allow/Block List for Teams domains and addresses](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-teams-domains-configure)<br>- [User-reported Teams items](https://learn.microsoft.com/en-us/defender-office-365/submissions-teams)<br>- [Teams messages in quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files#use-the-microsoft-defender-portal-to-manage-microsoft-teams-quarantined-messages) | - [Real-time detections](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about)<sup>\*</sup><br>- [User tags, including Priority account](https://learn.microsoft.com/en-us/defender-office-365/user-tags-about)<br>- [The Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page)<br>- SIEM integration from Office 365 Management APIs for **detections**. For more information, see [Microsoft Defender for Office 365 and Threat Investigation and Response schema](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-schema#microsoft-defender-for-office-365-and-threat-investigation-and-response-schema).<br>- [URL trace](https://learn.microsoft.com/en-us/defender-endpoint/investigate-domain)<br>- [Defender for Office 365 reports](https://learn.microsoft.com/en-us/defender-office-365/reports-defender-for-office-365)<br>- [Teams message entity panel](https://learn.microsoft.com/en-us/defender-office-365/teams-message-entity-panel) | - [Zero-hour auto purge \(ZAP\) for Teams](https://learn.microsoft.com/en-us/defender-office-365/zero-hour-auto-purge#zero-hour-auto-purge-zap-in-microsoft-teams) |

<sup>\*</sup> The presence of **Email & collaboration** > **Real-time detections** in the Microsoft Defender portal is a quick way to differentiate between Defender for Office 365 Plan 1 and Plan 2.

[![Screenshot of the Real-time detections selection in the Email & collaboration section in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/te-rtd-select-real-time-detections.png)](https://learn.microsoft.com/en-us/defender-office-365/media/te-rtd-select-real-time-detections.png#lightbox)

### Defender for Office 365 Plan 2 capabilities

Defender for Office 365 Plan 2 expands on the *investigation* and *response* capabilities of Plan 1 with the addition of *automation*.

The extra features that you get in **Defender for Office 365 Plan 2** on top of Defender for Office 365 Plan 1 are described in the following table:

| Prevent/Detect | Investigate | Respond |
| --- | --- | --- |
| - [Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started)<br>- [Priority account protection](https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-turn-on-priority-account-protection) | - [Threat Explorer \(Explorer\)](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about) instead of Real-time detections.<sup>\*</sup><br>- [Threat Trackers](https://learn.microsoft.com/en-us/defender-office-365/threat-trackers)<br>- [Campaigns](https://learn.microsoft.com/en-us/defender-office-365/campaigns)<br>- [Advanced hunting on Teams messages](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-messageevents-table) | - [Automated Investigation and Response \(AIR\)](https://learn.microsoft.com/en-us/defender-office-365/air-about):<br><br>  - AIR from Threat Explorer<br>  - AIR for compromised users<br><br>- SIEM Integration from Office 365 Management APIs for **automated investigations**. For more information, see [Automated investigation and response events in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-schema#automated-investigation-and-response-events-in-office-365).<br>- SIEM Integration from Office 365 Management APIs for **Attack simulation training**. For more information, see [Attack sim schema in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-schema#attack-sim-schema).<br>- SIEM Integration from Defender XDR APIs for **Advanced hunting**, **Incidents**, and **Streaming**. For more information, see [Overview of Microsoft Defender XDR APIs](https://learn.microsoft.com/en-us/defender-xdr/api-overview).<br>- [Remove users from Teams chats](https://learn.microsoft.com/en-us/defender-office-365/teams-message-entity-panel#remove-users-from-teams-chats-in-the-teams-message-entity-panel) |

<sup>\*</sup> The presence of **Email & collaboration** > **Explorer** in the Microsoft Defender portal is a quick way to differentiate between Defender for Office 365 Plan 2 and Plan 1.

[![Screenshot of the Explorer selection in the Email & collaboration section in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/te-rtd-select-threat-explorer.png)](https://learn.microsoft.com/en-us/defender-office-365/media/te-rtd-select-threat-explorer.png#lightbox)

## Defender for Office 365 Plan 1 vs. Plan 2 cheat sheet

This quick-reference section summarizes the different capabilities between Defender for Office 365 Plan 1 and Plan 2 that aren't included in the built-in security features for all cloud mailboxes.

To compare the different capabilities between Defender for Office 365 Plan 1 and Plan 2 **for Microsoft Teams**, see [Microsoft Defender for Office 365 support for Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-about).

| Defender for Office 365 Plan 1 | Defender for Office 365 Plan 2 |
| --- | --- |
| Prevent and detect capabilities:<br><br>- [Anti-phishing policies with impersonation protection and phishing email thresholds](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-about#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)<br>- [Safe Attachments](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-about), including [Safe Attachments for SharePoint, OneDrive, and Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-for-spo-odfb-teams-about)<br>- [Safe Links](https://learn.microsoft.com/en-us/defender-office-365/safe-links-about)<br>- [Tenant Allow/Block List for Teams](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-teams-domains-configure)<br>- [User-reported Teams items](https://learn.microsoft.com/en-us/defender-office-365/submissions-teams)<br><br>  <br>Investigate and respond capabilities:<br><br>- [Real-time detections](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about)<br>- [User tags, including Priority account](https://learn.microsoft.com/en-us/defender-office-365/user-tags-about)<br>- [The Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page)<br>- [Teams message entity panel](https://learn.microsoft.com/en-us/defender-office-365/teams-message-entity-panel)<br>- [ZAP for Teams](https://learn.microsoft.com/en-us/defender-office-365/zero-hour-auto-purge#zero-hour-auto-purge-zap-in-microsoft-teams) | Everything in Defender for Office 365 Plan 1  <br>  <br>--- plus ---  <br>  <br>Prevent and detect capabilities:<br><br>- [Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations)<br>- [Priority account protection](https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-turn-on-priority-account-protection)<br><br>  <br>Investigate and respond capabilities:<br><br>- [Threat Explorer \(Explorer\)](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about)<br>- [Threat Trackers](https://learn.microsoft.com/en-us/defender-office-365/threat-trackers)<br>- [AIR](https://learn.microsoft.com/en-us/defender-office-365/air-about)<br>- [Proactively hunt for threats with advanced hunting in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)<br>- [Investigate incidents in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents)<br>- [Investigate alerts in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts)<br>- [Advanced hunting on Teams messages](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-messageevents-table)<br>- [Remove users from Teams chats](https://learn.microsoft.com/en-us/defender-office-365/teams-message-entity-panel#remove-users-from-teams-chats-in-the-teams-message-entity-panel) |

- For more information, see [Feature availability across Defender for Office 365 plans](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- [Safe Documents](https://learn.microsoft.com/en-us/defender-office-365/safe-documents-in-e5-plus-security-about) is available to users with the Microsoft 365 A5 or Microsoft Defender Suite licenses \(not included in Defender for Office 365 plans\).
- If your current subscription doesn't include Defender for Office 365 Plan 2, you can [try Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365) free for 90 days. Or, [contact sales to start a trial](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html).
- Organizations with Defender for Office 365 Plan 2 have access to **Microsoft Defender integration** to efficiently detect, review, and respond to incidents and alerts.

## Related content

- [Get started with Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-deployment-guide)
- [Microsoft Defender for Office 365 Security Operations Guide](https://learn.microsoft.com/en-us/defender-office-365/mdo-sec-ops-guide)
- [Migrate from a non-Microsoft protection service or device to Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365)
- [What's new in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/defender-for-office-365-whats-new)
- [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20Defender%20for%20Office%20365) - Describes new features that are being added to Defender for Office 365.
