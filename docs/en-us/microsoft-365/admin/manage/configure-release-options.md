<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# Configure new Standard and Deferred release options for Microsoft 365

Microsoft 365 delivers updates continuously, enabling organizations to adopt new capabilities without large, infrequent upgrades. To help IT admins manage this pace of change, Microsoft 365 offers a new three-tier, audience-based release model—**Frontier, Standard release, and Deferred release**—so organizations can balance early access with readiness and control.

## Release options

Use these new release options to align feature delivery with your organization's readiness, governance requirements, and overall change management strategy.

Important

In November 2026, administrators can no longer add users to, remove users from, or modify Targeted release enrollment. In January 2027, Targeted release will be retired and no longer available to use. For more information, see [Plan for retirement of Targeted release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/targeted-release-retirement?view=o365-worldwide).

To prepare for this change, we recommend configuring Standard release and Deferred release options to manage when users in your organization receive generally available Microsoft 365 services as Microsoft delivers features through the new release model. If your organization has configured Targeted release in the Microsoft 365 admin center, you can continue using your existing configuration until its retired. Use the Message center to stay informed about updates delivered through the new audience-based release model.

### Frontier program

For pre-GA availability, [Frontier](https://www.microsoft.com/microsoft-365-copilot/frontier-program) provides preview access to innovative and emerging AI and now non-AI capabilities in Microsoft 365 before those features reach general availability. You can opt in users to both Frontier preview *and* assign them to Standard release or Deferred release. Users who are opted in to Frontier receive eligible Microsoft 365 features before general availability. For features that aren't part of Frontier, the user's existing Standard release or Deferred release preference determines when they receive features at GA.

For more information about getting started with the Frontier preview, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide).

### Standard release

With **Standard release**, your organization receives new features as soon as they're generally available \(GA\). Standard release should be the primary release channel for most customers. Microsoft thoroughly tests and validates all features and services before releasing them. Your organization is configured as Standard release by default.

### Deferred release

If you have additional validation requirements, consider using **Deferred release** for some or all users. Deferred release lets you delay [major updates](#what-qualifies-as-a-major-update) for specific users for approximately 30 days after rollout to the Standard release audience begins. After the 30-day period, generally available features are released to users in the Deferred release audience. In the Message center, features included in deferred release are tagged as both **Major update** and **Deferred feature**.

## How release validation works

Microsoft feature teams validate each new release first, followed by the Microsoft 365 feature team. Then, the feature rolls out to all of Microsoft. At each release phase, Microsoft collects feedback and further validates quality by monitoring key usage metrics before it goes to the public. This series of progressive validations helps make sure the worldwide rollout to general availability \(Standard release\) is as robust as possible.

As shown in the following figure, you can now use a modern, audience-based release model that includes the Frontier program, Standard release, and Deferred release as release options.

[![Figure displaying audience-based release audiences for Microsoft 365.](https://learn.microsoft.com/en-us/microsoft-365/media/audience-based-release-model.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/audience-based-model-expanded.png?view=o365-worldwide#lightbox)

For a comparison of release options, see the following table:

| Release audience | Primary purpose | Feature readiness | Key considerations for IT admins |
| --- | --- | --- | --- |
| **Frontier program** | Early experimentation and feedback | Pre-GA, not fully supported | You must opt in to access Frontier. Frontier features are preview, subject to change, and not governed by GA SLAs. IT admins can control which users have access to which Frontier features and agents. |
| **Standard release  <br>\(default\)** | Default GA rollout | Fully supported GA features | Features are supported, communicated through Message center and release notes, and expected to remain available under standard lifecycle policies. Recommended for most organizations. |
| **Deferred release** | Delayed GA for additional preparation | Fully supported GA features \(delayed\) | Same functionality as Standard release, delayed 30 days after Standard release \(GA\) for major updates. Consider if your organization has additional validation requirements. |

For significant updates, Microsoft first notifies you through the [AI at Work Roadmap](https://www.microsoft.com/microsoft-365/roadmap), formerly known as Microsoft 365 Roadmap. Before rollout, Microsoft notifies you through the [Microsoft 365 Message center](https://go.microsoft.com/fwlink/p/?linkid=2070717).

### What qualifies as a major update

Major updates are communicated at least 30 days in advance when an action is required and might include:

- User impacting changes to daily productivity such as changing a user's inbox, meetings, delegations, sharing and access that might result in help desk calls, or organizational conformance concerns.
- Changes to the themes, web parts, deployed Copilot agents, and other components that might impact customer customizations.
- Increases or decreases to visible capacity such as storage, number of rules, Copilot agents and prompts, items, or durations.
- Rebranding that might cause end-user confusion or result in help desk changes, collateral changes, or URL changes if the new URL isn't \*.cloud.microsoft
- A new service or application deployed with default settings turned on.
- Changes to where data is stored or accessed.

In the Message center, major updates are tagged as **Major update**. For more information about the Message center, see [Message center in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/message-center?view=o365-worldwide).

## Prerequisites

To configure Standard release and Deferred release options, you need one of the following roles in the Microsoft 365 admin center:

- Office Apps Admin
- Security Admin
- AI Admin

For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

### Security groups

To manage group-based exceptions, create or identify a dedicated Microsoft Entra ID security group to use for that release option. For more information about security groups, review the following articles:

- [Learn about groups](https://learn.microsoft.com/en-us/entra/fundamentals/concept-learn-about-groups)
- [Manage groups with Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups)
- [Manage groups with Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/entra/identity/users/groups-settings-v2-cmdlets)

## Release option best practices

To balance early access with organizational readiness, use the release options in the following ways:

- Enroll your organization in Standard release to get the latest Microsoft 365 improvements as soon as they reach general availability. Optionally, assign business-critical users to Deferred release to give them more time to prepare for major changes.
- Use Deferred release if you need extra time to validate deferred-capable features before broad rollout. Assign a subset of IT pros or power users to Standard release to evaluate new features for privacy and compliance readiness.
- Plan release phases around user impact and readiness, not individual feature controls, to help manage risk and set clear expectations for users.
- Align your release configuration with your change management and support readiness, including documentation, training, and help desk preparation.
- Review and adjust audience assignments over time as your organization's readiness and change tolerance evolve.

## Configure general availability release options in Microsoft 365 admin center

Important

For customers in GCC, GCC High, and DoD environments, Standard release \(general availability\) remains the supported release option following the [retirement of Targeted release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/targeted-release-retirement?view=o365-worldwide). Currently, Deferred release and Frontier aren't available in government cloud environments. Check this article for future updates regarding availability.

By default, use Standard release for Microsoft 365 service updates. This option meets the needs of most customers. To better manage your organization's readiness and testing needs, you can change the default release selection to Deferred release at any time in the Microsoft 365 admin center. It can take up to 24 hours for the following changes to take effect in Microsoft 365.

To assign users or [security groups](https://learn.microsoft.com/en-us/entra/fundamentals/concept-learn-about-groups) to Deferred release, follow these steps:

1. Sign in to the Microsoft 365 admin center.
2. In the left navigation, expand **Copilot** and select **Settings**.

   [![Screenshot of Copilot settings in Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/copilot-settings-admin-center.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/copilot-settings-admin-center-expanded.png?view=o365-worldwide#lightbox)
3. Under the **All Settings** tab, select **Copilot release preferences: General Availability**.
4. Choose either **Standard release** or **Deferred release**.
5. Add any user or security group exceptions. You can add up to 100 exceptions to Standard release or Deferred release. Each user in a security group and each user added individually count toward the 100-user limit.

   - If you want to assign only a specific user or security group to Deferred release, select **Standard release**, search for the user or group, and select their name.

     ![Screenshot of Standard release in Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/audience-release-options-standard.png?view=o365-worldwide)
   - If you want to assign only a specific user or security group to Standard release, select **Deferred release**, search for the user or group, and select their name.

6. Select **Save**.

To opt in to Frontier preview, follow the instructions in [Configure Frontier preview for Microsoft 365 services](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide).

Note

If you move users from Standard release to Deferred release, they might lose access to features that aren't available yet in Deferred release.

## Related articles

[Modern change management for Microsoft 365 - Overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/plan-for-change-management?view=o365-worldwide)

[Get started with the Microsoft Release Communications MCP Server](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/mrc-mcp?view=o365-worldwide)

[Overview of Microsoft MCP Server for Enterprise](https://learn.microsoft.com/en-us/graph/mcp-server/overview)

[Get started with Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide)

[What's new in Message center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/message-center-updates?view=o365-worldwide)

[Plan for the retirement of Targeted release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/targeted-release-retirement?view=o365-worldwide)
