<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/tune-microsoft-defender-for-office-365 -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# Tune Microsoft Defender for Office 365 security controls and thresholds

When a relevant license is enabled, Microsoft Defender for Office 365 protects collaboration across Exchange Online, Teams, SharePoint, OneDrive, and Microsoft 365 applications by default. However, you can do some "tuning" for maximum benefit.

The term "tuning" is used often and can mean different things. For example:

- [Configuring security controls](#configuring-security-controls) or [configuring connectors for complex routing and dual filtering scenarios](#complex-routing-and-dual-filtering-scenarios) as part of initial setup.
- Setting [security control thresholds](#security-control-thresholds) \(for example, the bulk email slider and the advanced filtering slider\) to determine how aggressively email is blocked.
- Adding and managing [customer configured allows and blocks](#customer-configured-allows-and-blocks). Allows are a powerful tool for managing email deliverability but can let malicious or unwanted email be delivered if not correctly managed. Blocks ensure unwanted email isn't delivered but can lead to user productivity loss.
- [Submissions and system learning](#submissions-and-system-learning), or how the filtering stack self corrects based on the submission of false positive and false negative email.

## Configuring security controls

The easiest and safest way to configure security controls is by onboarding to [preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies). By using the Standard or Strict preset security policies, you always have Microsoft's recommended, best practice configuration for users. For instructions, see [Steps to set up the Standard or Strict preset security policies for Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies).

Are you worried about attacks targeting your CEO, CIO, or CFO? You can [manage and monitor priority accounts in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/security-and-compliance/priority-accounts).

If you use custom security policies, configuration analyzer gives recommendations to make sure you follow Microsoft's best practices. You can [Optimize and correct threat policies with configuration analyzer](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/optimize-and-correct-security-policies-with-configuration-analyzer).

## Complex routing and dual filtering scenarios

Using a non-Microsoft email filtering solution with Defender for Office 365 requires some extra configuration to ensure you're getting the best from both filtering solutions. For more information, see [Getting started with defense in-depth configuration for email security](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/defense-in-depth-guide). You need to be careful when using connectors to route mail to ensure that Defender for Office 365 has access to the original email sender information. To meet this requirement, configure [Enhanced filtering for connectors in Exchange Online](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

## Security control thresholds

The bulk email slider and the phishing email threshold slider allow you to determine how aggressively each of those filters is applied. To optimize the threshold where bulk mail is treated as spam, you can [Assess and tune your filtering for bulk mail in Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/tune-bulk-mail-filtering-walkthrough). [Recommended email and collaboration threat policy settings for cloud organizations](https://learn.microsoft.com/en-us/defender-office-365/recommended-settings-for-eop-and-office365#phishing-email-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) contains best practices for choosing the right [Phishing email threshold](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-about#phishing-email-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) for your organization.

## Customer configured allows and blocks

Overrides are a powerful tool that can be used to deliver or block email regardless of how Defender for Office 365 evaluates the message. [Understanding overrides within the email entity page in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/understand-overrides-in-email-entity) provides a guide for using the email entity page to understand why a message was allowed or blocked across all the different types of available overrides.

### How submissions and system learning affect allows and blocks

The single most important thing you can do to improve the accuracy of email filtering for users is to [Report spam, non-spam, phishing, suspicious email and files to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-report-messages-files-to-microsoft). This information informs the Microsoft Security Analyst team what changes need to be made across the entire filtering stack to ensure users have the best possible experience. Here are some best practices for [How to handle malicious emails that are delivered to recipients using Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/how-to-handle-false-negatives-in-microsoft-defender-for-office-365) and [How to handle legitimate emails getting blocked from delivery using Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/how-to-handle-false-positives-in-microsoft-defender-for-office-365).

## Related content

[Microsoft Defender for Office 365 Overview](https://learn.microsoft.com/en-us/defender-office-365/mdo-about)
