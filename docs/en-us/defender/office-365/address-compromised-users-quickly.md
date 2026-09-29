<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/address-compromised-users-quickly -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Address compromised user accounts with automated investigation and response

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

[Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet) includes powerful [automated investigation and response](https://learn.microsoft.com/en-us/defender-office-365/air-about) \(AIR\) capabilities. Such capabilities can save your security operations team a lot of time and effort dealing with threats. This article describes one of the facets of the AIR capabilities, the compromised user security playbook.

The compromised user security playbook enables your organization's security team to:

- Speed up detection of compromised user accounts;
- Limit the scope of a breach when an account is compromised; and
- Respond to compromised users more effectively and efficiently.

## Review alerts for compromised users

When a user account is compromised, atypical or anomalous behaviors occur. For example, phishing and spam messages might be sent internally from a trusted user account. Defender for Office 365 can detect such anomalies in email patterns and collaboration activity within Office 365. When Defender for Office 365 detects these anomalies, alerts are triggered, and the threat mitigation process begins.

## Investigate and respond to a compromised user

When Defender for Office 365 detects signs that a user account is compromised, it triggers alerts. In some cases, that user account is blocked and prevented from sending any further email messages until the issue is resolved by your organization's security operations team. In other cases, an automated investigation begins which can result in recommended actions that your security team should take.

Important

You must have appropriate permissions to perform the following tasks. For more information, see [Required permissions to use AIR capabilities](https://learn.microsoft.com/en-us/defender-office-365/air-about#required-permissions-and-licensing-for-air).

Use the following procedures to investigate and respond to a compromised user:

- [View and investigate restricted users](#view-and-investigate-restricted-users)
- [View details about automated investigations](#view-details-about-automated-investigations)

Watch this short video to learn how you can detect and respond to user compromise in Microsoft Defender for Office 365 using Automated Investigation and Response \(AIR\) and compromised user alerts.

<iframe src="https://learn-video.azurefd.net/vod/player?id=efb1e40c-dc48-42ea-a73c-1811a3913192" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

### View and investigate restricted users

You have a few options for navigating to a list of restricted users. For example, in the Microsoft Defender portal, you can go to **Email & collaboration** > **Review** > **Restricted Users**. The following procedure describes navigation using the **Alerts** dashboard, which is a good way to see various kinds of alerts that might have been triggered.

1. Open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com) and go to **Incidents & alerts** > **Alerts**. Or, to go directly to the **Alerts** page, use [https://security.microsoft.com/alerts](https://security.microsoft.com/alerts).
2. On the **Alerts** page, filter the results by time period and the policy named **User restricted from sending email**.

   [![The Alerts page in the Microsoft Defender portal filtered for restricted users](https://learn.microsoft.com/en-us/defender-office-365/media/m365-sc-alerts-page-with-restricted-user.png)](https://learn.microsoft.com/en-us/defender-office-365/media/m365-sc-alerts-page-with-restricted-user.png#lightbox)
3. If you select the entry by clicking on the name, a **User restricted from sending email** page opens with additional details for you to review. Next to the **Manage alert** button, you can click ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-more-actions.png) **More options** and then select **View restricted user details** to go to the **Restricted users** page, where you can [release the restricted user](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-restore-restricted-users).

[![The User restricted from sending email page](https://learn.microsoft.com/en-us/defender-office-365/media/m365-sc-alerts-user-restricted-from-sending-email-page.png)](https://learn.microsoft.com/en-us/defender-office-365/media/m365-sc-alerts-user-restricted-from-sending-email-page.png#lightbox)

### View details about automated investigations

When an automated investigation has begun, you can see its details and results in the **Action center** in the Microsoft Defender portal.

For detailed instructions on viewing automated investigation results, see [View details of an investigation](https://learn.microsoft.com/en-us/defender-office-365/air-view-investigation-results).

## Important considerations for automated investigation and response

Keep the following guidance in mind when investigating and responding to compromised users:

- **Stay on top of your alerts**. As you know, the longer a compromise goes undetected, the larger the potential for widespread impact and cost to your organization, customers, and partners. Early detection and timely response are critical to mitigate threats, and especially when a user's account is compromised.
- **Automation assists your security operations team**. Automated investigation and response capabilities can detect a compromised user early on and enable your security operations team to take action to remediate the threat. For help reviewing or approving remediation actions, see [Review and approve actions](https://learn.microsoft.com/en-us/defender-office-365/air-review-approve-pending-completed-actions).

## Related resources

- [Review the required permissions to use AIR capabilities](https://learn.microsoft.com/en-us/defender-office-365/air-about#required-permissions-and-licensing-for-air)
- [Find and investigate malicious email in Office 365](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-investigate-delivered-malicious-email)
- [Learn about AIR in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [Microsoft 365 Roadmap for Defender for Office 365](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20Defender%20for%20Office%20365)
