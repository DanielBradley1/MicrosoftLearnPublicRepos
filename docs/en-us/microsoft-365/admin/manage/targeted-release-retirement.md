<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/targeted-release-retirement?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Plan for the retirement of Targeted release in Microsoft 365

Important

In January 2027, Microsoft is retiring Targeted release for Microsoft 365 services as part of a broader effort to simplify how organizations manage Microsoft 365 feature releases.

In November 2026, administrators can no longer add users to, remove users from, or modify Targeted release enrollment. Microsoft 365 feature updates that currently use Targeted release will transition to Frontier, Standard release, and Deferred release preferences. Users assigned to Targeted release will remain in Targeted release until its retirement. Users will then default to receiving features through their [modern release preferences](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide). Use the Message center to stay informed about updates delivered through the new audience-based release model.

Microsoft is retiring Targeted release for Microsoft 365 services as part of a broader effort to simplify how organizations manage Microsoft 365 feature releases by moving to our streamlined audience-based release model. If your organization is configured for Targeted release, review your release preferences before January 2027 to help ensure users continue receiving Microsoft 365 updates to align with your organization's change management, validation, and feature rollout strategy.

Our audience-based release model includes the following release options in the Microsoft 365 admin center:

- **Frontier**: Users receive early access to eligible Microsoft 365 features *before* general availability \(GA\) for experimentation, preview validation, and feedback.
- **Standard release**: By default, users receive access to Microsoft 365 features as they become generally available.
- **Deferred release**: Users receive access to Microsoft 365 major features after they have been generally available for approximately 30 days, giving organizations more time to prepare.

After Targeted release is retired, manage general availability release timing through Standard release and Deferred release. Users who are opted in to Frontier receive eligible Microsoft 365 features before general availability. For features that aren't part of Frontier, the user's existing Standard release or Deferred release preference continues to determine when they receive features at GA.

For more information about general availability release options, see [Configure Standard and Deferred release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide). If you want to also receive early, pre-GA access to new features, you can opt in specific users or tenants to the [Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide).

## Prepare for the change

This change affects organizations that currently have configured Targeted release in the Microsoft 365 admin center. Until Targeted release is retired, users and tenants currently assigned to Targeted release continue to receive eligible Targeted release features. If you use Targeted release and don't update your release preferences before its retirement, users assigned to Targeted release default to receiving features through your current modern release preference for general availability \(Standard release or Deferred release\).

This change applies only to Microsoft 365 services that currently deliver features through Targeted release, including the Microsoft 365 admin center, Microsoft Teams, OneDrive, SharePoint Online, Outlook on the web, New Outlook for Windows, and Office for the web. Microsoft 365 Apps update channels, Windows update channels, and Microsoft 365 Insider programs aren't affected. Existing Microsoft 365 services and functionality continue to operate normally. Message center continues to tag features that are part of Targeted release, Standard, Deferred, and Frontier releases accordingly.

If your organization doesn't use Targeted release, no immediate action is required. However, administrators should become familiar with Frontier, Standard release, and Deferred release as Microsoft expands this release model across Microsoft 365.

Important

For customers in GCC, GCC High, and DoD environments, Standard release \(general availability\) remains the supported release option following the retirement of Targeted release. Currently, Deferred release and Frontier aren't available in government cloud environments. Check this article for future updates regarding availability.

### Key dates

**Now**

- In the Microsoft 365 admin center, review modern GA \(Standard release and Deferred release\) release preferences to help ensure users currently enrolled in Targeted release continue receiving Microsoft 365 updates after its retirement according to your organization's desired change management strategy.
- Enroll users in Frontier, Standard release, Deferred release \(if needed\). See [Recommended actions](#recommended-actions) below.

**November 2026**

- Administrators can no longer add users to, remove users from, or modify Targeted release enrollment.
- If you need to make any updates to modern release preferences, you can configure Frontier, Standard release, Deferred release preferences in one location using the new unified Release Preferences experience in the Microsoft 365 admin center.

**January 2027**

- Microsoft retires Targeted release for Microsoft 365 services.
- Targeted Release user and tenant assignments are no longer used for Microsoft 365 feature delivery in applicable Microsoft 365 services.
- Users previously assigned to Targeted release start to receive updates according to the modern release preferences \(Frontier, Standard release, Deferred release\).

## Release preferences in Microsoft 365 admin center

Use the following table to configure the Standard or Deferred release preference based on your current Targeted release configuration in the Microsoft 365 admin center. Refer to the [recommended actions](#recommended-actions) section for the location of these preferences in the Microsoft 365 admin center.

| Current release preference \(before retirement\) | Recommended new release preference \(after retirement\) |
| --- | --- |
| **Targeted release for everyone** | - If users should receive eligible features as soon as they reach general availability, choose **Standard release**.  <br>- If additional time is needed to prepare for eligible major changes, use **Deferred release**. |
| **Targeted release for select users** | To preserve using an early production validation group while giving your broader organization additional time to prepare:  <br>- Choose **Deferred release**  <br>- Under **Assign users or groups for standard release**, add validation, support, or pilot users. |
| **Standard release for everyone** | No update is required. **Standard release** is the default release preference. |

For more information, see [Configure new Standard and Deferred release options for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide).

## Recommended actions

Before November 2026, we recommend doing the following actions:

1. In the Microsoft 365 admin center, **review and identify** current users assigned to Targeted release under **Settings** > **Org settings** > **Organization profile** > **Release preferences**.
2. **Review and configure** [Standard release or Deferred release preferences](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide) under **Copilot** > **Settings** > **View all** > **Copilot Release preferences: General availability**. For recommendations, see the [Release preferences in Microsoft 365 admin center](#release-preferences-in-microsoft-365-admin-center) section of this article.
3. **Review and configure** [Frontier](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide) preview preferences under **Copilot** > **Settings** > **View all** > **Copilot Frontier**.
4. **Update** internal documentation and processes that reference Targeted release.
5. **Notify** change management teams, support teams, security and compliance teams, pilot groups, and key IT stakeholders about the upcoming retirement.

Completing these actions before November 2026 helps ensure a smooth transition and prevents disruption to existing validation, testing, and readiness processes.

In November 2026, release preferences for Frontier, Standard release, and Deferred release can be managed through the unified release preferences experience in the Microsoft 365 admin center. The current experience for managing Standard release and Deferred release preferences will be retired when the unified release preferences experience becomes available. Additional details about related admin experience changes will be shared in Message center.

## Next step

To configure your organization's general availability release preferences for Microsoft 365 updates, follow the instructions in [Configure Standard and Deferred release preferences](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide). For answers to frequently asked questions about Targeted release and its retirement, see [Frequently asked questions about modern release options for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/release-options-faq?view=o365-worldwide).

## Related articles

[Configure modern release preferences in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide)

[Frequently asked questions about modern release options for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/release-options-faq?view=o365-worldwide)

[Get started with the Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide)

[Overview of modern change management in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/plan-for-change-management?view=o365-worldwide)
