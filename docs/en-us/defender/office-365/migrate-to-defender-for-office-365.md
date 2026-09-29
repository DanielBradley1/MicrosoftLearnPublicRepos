<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# Migrate from a non-Microsoft protection service or device to Microsoft Defender for Office 365

If you already have an existing non-Microsoft protection service or device that sits in front of Microsoft 365, you can use this guide to migrate your protection to Microsoft Defender for Office 365. Defender for Office 365 gives you the benefits of a consolidated management experience, potentially reduced cost \(using products that you already pay for\), and a mature product with integrated security protection. For more information, see [Microsoft Defender for Office 365](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Watch this short video to learn more about migrating to Defender for Office 365.

<iframe src="https://learn-video.azurefd.net/vod/player?id=41c64de1-92ce-4ff6-9660-557a4d6f74f1" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

This guide provides specific and actionable steps for your migration, and assumes the following facts:

- You already have cloud mailboxes, but you're currently using a non-Microsoft service or device for email protection. Mail from the internet flows through the protection service before delivery into your Microsoft 365 organization. Microsoft 365 protection is as low as possible \(it's never completely off. For example, malware protection is always enforced\).

  [![The Mail flows from the internet through the non-Microsoft protection service or device before delivery into Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-before.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-before.png#lightbox)
- You're beyond the investigation and consideration phase for protection by Defender for Office 365. If you need to evaluate Defender for Office 365 to decide whether it's right for your organization, we recommend the options described in [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).
- You already purchased Defender for Office 365 licenses.
- You need to retire your existing non-Microsoft protection service, which means you ultimately need to point the MX records for your email domains to Microsoft 365. When you're done, mail from the internet flows directly into Microsoft 365 and is protected by Defender for Office 365.

  [![The mail flows from the internet into Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-after.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-after.png#lightbox)

Eliminating your existing protection service in favor of Defender for Office 365 is a significant step that you shouldn't take lightly. Nor should you rush to make the change. The guidance in this migration guide helps you transition your protection in an orderly manner with minimal disruption to your users.

The high-level migration steps are illustrated in the following diagram. The actual steps are listed in the section named [The migration process](#the-migration-process) later in this article.

[![The process of migration from a non-Microsoft protection solution or device to Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-overview.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-overview.png#lightbox)

Tip

For information about configuring protection for Microsoft Teams, see the following articles:

- [Microsoft Defender for Office 365 support for Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-about)
- [Quickly configure Microsoft Teams protection in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-quick-configure)
- [Security Operations Guide for Teams protection in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-sec-ops-guide)

## Why use the steps in this guide?

In the IT industry, surprises are bad. Simply flipping your MX records to point to Microsoft 365 without prior and thoughtful testing will result in many surprises. For example:

- You or your predecessors probably spent time and effort customizing your existing protection service for optimal mail delivery. In other words, blocking what needs to be blocked, and allowing what needs to be allowed. It's almost a guaranteed certainty that not every customization in your current protection service is required in Defender for Office 365. It's also possible that Defender for Office 365 will introduce new issues \(allows or blocks\) that didn't happen or weren't required in your current protection service.
- Your help desk and security personnel need to know what to do in Defender for Office 365. For example, if a user complains about a missing message, does your help desk know where or how to look for it? They're likely familiar with the tools in your existing protection service, but what about the tools in Defender for Office 365?

In contrast, if you follow the steps in this migration guide, you get the following tangible benefits for your migration:

- Minimal disruption to users.
- Objective data from Defender for Office 365 that you can use to report on the progress and success of the migration to management.
- Early involvement and instruction for help desk and security personnel.

The more you familiarize yourself with how Defender for Office 365 will affect your organization, the better the transition will be for users, help desk personnel, security personnel, and management.

This migration guide gives you a plan for gradually "turning the dial." You can monitor and test how Defender for Office 365 affects users and their email so you can react quickly to any issues.

## The migration process

The process of migrating from a non-Microsoft protection service to Defender for Office 365 can be divided into three phases as described in the following table:

[![The process for migrating to Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/media/phase-diagrams/migration-phases.png)](https://learn.microsoft.com/en-us/defender-office-365/media/phase-diagrams/migration-phases.png#lightbox)

| Phase | Description |
| --- | --- |
| [Prepare for your migration](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare) | n<br><br>1. [Inventory the settings at your existing protection service](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare#inventory-the-settings-at-your-existing-protection-service)<br>2. [Check your existing protection configuration in Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare#check-your-existing-protection-configuration-in-microsoft-365)<br>3. [Check your mail routing configuration](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare#check-your-mail-routing-configuration)<br>4. [Move features that modify messages into Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare#move-features-that-modify-messages-into-microsoft-365)<br>5. [Define spam and bulk user experiences](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare#define-spam-and-bulk-user-experiences)<br>6. [Identify and designate priority accounts](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare#identify-and-designate-priority-accounts) |
| [Set up Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-setup) | 1. [Create distribution groups for pilot users](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-setup#step-1-create-distribution-groups-for-pilot-users)<br>2. [Configure user reported message settings](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-setup#step-2-configure-user-reported-message-settings)<br>3. [Maintain or create the bypass spam filtering mail flow rule](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-setup#step-3-maintain-or-create-the-bypass-spam-filtering-mail-flow-rule)<br>4. [Configure Enhanced Filtering for Connectors](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-setup#step-4-configure-enhanced-filtering-for-connectors)<br>5. [Create pilot threat policies](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-setup#step-5-create-pilot-threat-policies) |
| [Onboard to Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard) | 1. [Begin onboarding Security Teams](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-1-begin-onboarding-security-teams)<br>2. [\(Optional\) Exempt pilot users from filtering by your existing protection service](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)<br>3. [Tune spoof intelligence](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-3-tune-spoof-intelligence)<br>4. [Tune impersonation protection and mailbox intelligence](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-4-tune-impersonation-protection-and-mailbox-intelligence)<br>5. [Use data from user reported messages to measure and adjust](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-5-use-data-from-user-reported-messages-to-measure-and-adjust)<br>6. [\(Optional\) Add more users to your pilot and iterate](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-6-optional-add-more-users-to-your-pilot-and-iterate)<br>7. [Extend Microsoft 365 protection to all users and turn off the bypass spam filtering mail flow rule](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-bypass-spam-filtering-mail-flow-rule)<br>8. [Switch your MX records](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-onboard#step-8-switch-your-mx-records) |

## Next step

- Proceed to [Phase 1: Prepare](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365-prepare).
