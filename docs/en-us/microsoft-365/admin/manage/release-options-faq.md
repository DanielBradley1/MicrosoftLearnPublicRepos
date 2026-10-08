<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/release-options-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Frequently asked questions about modern release options for Microsoft 365

This article provides answers to frequently asked questions that IT admins might have about release options in Microsoft 365. For more information about modern release options in Microsoft 365, see [Modern change management for Microsoft 365 - Overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/plan-for-change-management?view=o365-worldwide) and [Configure modern release options](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide).

Note

Deferred release only supports features tagged in Message center posts as both **Major update** *and* **Deferred feature**.

## Can I choose which users get Microsoft 365 features earlier vs later?

Yes, within the same tenant, you can choose from the following options:

- Assign most users to Standard release and assign a subset of users to Deferred release, or
- Assign most users to Deferred release and assign a small group of early adopters to Standard release

This allows you to:

- Test changes with IT or pilot groups first
- Give business-critical users more time before receiving changes

## Can I defer individual features?

No, you can't defer individual features. Deferred release applies to eligible major features that Microsoft identifies as a **Deferred feature** and **Major update** in Message center.

If your tenant is configured for Deferred release, all eligible major features follow the deferred timeline automatically.

You can still use existing admin controls \(when available\) to manage specific features in your tenant.

## When does the 30-day deferred period begin?

The 30-day timer starts when the feature *begins* rolling out in GA to standard release users globally. The deferred period doesn't begin when the standard global rollout completes. Standard users can begin evaluating the feature immediately, but users that are in Deferred release receive the feature 30 days later.

## What if feature rollout takes weeks or months to reach all users?

Microsoft rolls out Microsoft 365 features in stages to help ensure quality.

When we roll out a feature for general availability, Standard release users receive the feature before Deferred release users. Users assigned to Standard release can start evaluating the feature as soon as it reaches your Standard release users.

Deferred release users receive the deferred-capable feature 30 days after the rollout to Standard release begins. This delay gives IT admins and power users more time to test, validate, and prepare before the feature reaches your Deferred release users.

## Will tenant-wide features respect standard and deferred user settings?

Most Microsoft 365 features are delivered at the user level and respect your Standard release and Deferred release assignments. However, some features are deployed at the tenant level. Tenant-wide changes might apply to all users at once, regardless of release audience assignment.

## What happens if a feature needs to be rolled back?

If Microsoft finds a quality issue during rollout:

- Microsoft pauses the rollout.
- Users who haven't received the feature won't get it.
- If needed, Microsoft might remove the feature from users who already received it.

Deferred release users won't receive a feature that Microsoft rolls back before it reaches them.

## Does Deferred release replace admin controls?

No, Deferred release provides time to evaluate production-ready, generally available features. It works alongside existing admin controls, feature-level enable/disable settings \(when available\).

You can still request additional controls through your Microsoft account team if needed.

## How does Message center support Deferred release?

For Deferred release, we've updated the Message center to do the following actions:

- Clearly identify deferred-eligible features with **Deferred release** label.
- Include a **Rollout timing** column to help you plan for updates
- Send out announcements closer to the start of GA to ensure accuracy

These updates can help reduce shifting timelines, improve readiness planning, and align communications with generally available and fully supported features. For information about Message center updates, see [What's new in Message center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/message-center-updates?view=o365-worldwide).

## Can I assign most of my organization to standard release and specific users to Deferred release?

Yes, if your organization needs more time for validating deferred-capable features, you can leverage assigning specific users to Deferred release in the audience-based release model. For more information about configuring modern release options, see [Configure modern release options for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide).

## Does Deferred release apply to features that aren't major updates?

No, even if you have users in Deferred release, a feature that isn't classified as a **Major update** and **Deferred feature** via Message center still releases to users when the feature is broadly available.

## How does Deferred release affect Frontier features?

Deferred release doesn't apply to Frontier program features. Deferred release enables customers to delay delivery of eligible features at general availability \(GA\). Frontier provides preview access for early adopters to evaluate new experiences and provide feedback. Frontier access is managed separately from Deferred release. Although Frontier features are preview \(pre-GA\), they run within an otherwise generally available \(GA\) environment. For more information, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide).

## Where can I find guidance on these new features and updates?

Check for updates to this article, [Modern change management for Microsoft 365 - Overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/plan-for-change-management?view=o365-worldwide), Message Center posts, and the [AI at Work Roadmap](https://www.microsoft.com/microsoft-365/roadmap), formerly known as the Microsoft 365 Roadmap, for more information about modern change communications coming to Microsoft 365.

## Do Standard release and Deferred release options affect Microsoft 365 App release options?

No. For information about release options for Microsoft 365 Apps, see [Overview of update channels for Microsoft 365 Apps](https://learn.microsoft.com/en-us/deployoffice/overview-update-channels).

## Does the retirement of Targeted release affect other update channels?

No. This change only applies to Microsoft 365 release preferences. Microsoft 365 Apps update channels, Windows update channels, and Microsoft 365 Insider programs aren't affected.

## What's happening to Targeted release?

In November 2026, administrators can no longer add, remove, or modify Targeted release assignments. In January 2027, Targeted release will be retired and no longer available to use. If you're currently using Targeted release, you can continue to do so until its retirement. We recommend configuring release preferences for Frontier, Standard release, and Deferred release audiences to align with the new release model as Microsoft begins delivering an increasing number of major features through it over time. Use the [Message center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/message-center?view=o365-worldwide) to keep up with new products and services using this audience-based release model. For more information about the retirement of Targeted release, see [Plan for the retirement of Targeted release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/targeted-release-retirement?view=o365-worldwide).

For more information about Standard release and Deferred release, see [Configure standard release and deferred release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide). For more information about the Frontier program, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide).

## If my organization only has a subset of users in Targeted release, how should I align with the new release model of with Standard release and Deferred release?

To preserve your early-validation pattern, enroll your tenant in Deferred release to provide additional time for readiness, validation, and change management, and assign a subset of users to Standard release for immediate access to eligible features at general availability.

## If my organization's entire tenant is in Targeted release, how should I align with the new release model of with Standard release and Deferred release?

To have your tenant receive eligible features as soon as they reach general availability, choose to have your tenant in Standard release. Optionally, to give some users additional time to prepare for major changes, assign specific users to Deferred release.

## What happens if I take no action regarding the retirement of Targeted release?

Users and tenants currently assigned to Targeted release will continue receiving eligible Targeted release features until Targeted Release is retired. After retirement, Targeted release assignments will no longer be used for feature delivery. Users and tenants will follow their configured Standard release or Deferred release preference. If no modern release preference is configured, users receive features through Standard release. Before Targeted release enrollment changes are disabled in November 2026, administrators should review their release preferences in the Microsoft 365 admin center to help ensure users continue receiving Microsoft 365 updates according to their organization's desired rollout strategy.

## Will Microsoft automatically update my release preference settings?

No, Microsoft won't automatically modify your release preference settings.

## How long will users continue receiving Targeted release features?

Users and tenants currently assigned to Targeted release continue to receive eligible Targeted Release features until Targeted release is retired.

## Can I add or remove users from Targeted release after November 2026?

No. In November 2026, administrators can no longer add users to, remove users from, or modify Targeted release assignments. Organizations should review their Targeted release users and release preferences before enrollment changes before this date.

## Does the retirement of Targeted release affect existing Microsoft 365 functionality?

No. This change affects how organizations manage Microsoft 365 feature release preferences. Existing Microsoft 365 services and functionality continue to operate normally.

## Related articles

[Configure modern release options for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide)

[Get started with Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide)

[Modern change management for Microsoft 365 - Overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/plan-for-change-management?view=o365-worldwide)

[Get started with the Microsoft Release Communications MCP Server](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/mrc-mcp?view=o365-worldwide)

[Plan for the retirement of Targeted release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/targeted-release-retirement?view=o365-worldwide)
