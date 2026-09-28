<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# Configure new Standard and Deferred release options for Microsoft 365

Microsoft 365 delivers updates continuously, enabling organizations to adopt new capabilities without large, infrequent upgrades. To help IT admins manage this pace of change, Microsoft 365 offers a new three-tier, audience-based release model—**Frontier, Standard, and Deferred**—so organizations can balance early access with readiness and control.

Important

The modern release options of standard and deferred initially only apply to Microsoft Copilot updates that are identified as both a major update and deferred capable in the Message center. Microsoft will expand this approach across all Microsoft 365 services over time. For release information for Microsoft 365 apps, see [Overview of update channels for Microsoft 365 Apps](https://learn.microsoft.com/en-us/deployoffice/overview-update-channels).

With **Standard release**, your organization receives new features as soon as they're generally available \(GA\). Standard release is the default option and should be the primary release channel for most customers. Microsoft thoroughly tests and validates all features and services before releasing them. Your organization is configured as standard release by default.

If you have additional validation requirements, consider **Deferred release** for all or some users. Features available in deferred release are [major updates](#what-qualifies-as-a-major-update) and are considered "deferred-capable," meaning admins have 30 days to prepare for the release after broad release in standard begins. After 30 days, generally available features appear to your users. These features are tagged with "Deferred feature" in the Message center.

For pre-release availability, the [Microsoft Frontier program](https://www.microsoft.com/microsoft-365-copilot/frontier-program) provides early access to innovative and emerging AI capabilities in Microsoft 365 before those features reach general availability. For more information about getting started with the Frontier program, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide).

Use these new release options to align feature delivery with your organization's readiness, governance requirements, and overall change management strategy.

Note

Currently, the modern release options of standard and deferred release channels aren't available for GCC, GCC High, and DoD cloud environments. These cloud environments can continue to use the existing [targeted and standard release options](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide). Check this article for updates regarding future support.

## How release validation works

Microsoft feature teams validate each new release first, followed by the Microsoft 365 feature team. Then, the feature rolls out to all of Microsoft. At each release phase, Microsoft collects feedback and further validates quality by monitoring key usage metrics before it goes to the public. This series of progressive validations helps make sure the worldwide rollout to general availability \(standard release\) is as robust as possible.

As shown in the following figure, you can now use a modern, audience-based release model that includes the Frontier program, Standard release, and Deferred release as release options.

[![Figure displaying audience-based release audiences for Microsoft 365.](https://learn.microsoft.com/en-us/microsoft-365/media/audience-based-release-model.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/audience-based-model-expanded.png?view=o365-worldwide#lightbox)

For a comparison of release options, see the following table:

| Release audience | Primary purpose | Feature readiness | Key considerations for IT admins |
| --- | --- | --- | --- |
| Frontier program | Early experimentation and feedback | Pre-GA, not fully supported | Frontier features are pre-release, subject to change, and not governed by GA SLAs. IT admins can control which users have access to which Frontier features and agents. |
| Standard release  <br>\(default\) | Default GA rollout | Fully supported GA features | Features are supported, communicated through Message Center and release notes, and expected to remain available under standard lifecycle policies. Recommended for most organizations. |
| Deferred release | Delayed GA for additional preparation | Fully supported GA features \(delayed\) | Same functionality as standard release, delayed 30 days after standard GA for major updates. Consider if your organization has additional validation requirements. |

For significant updates, Microsoft first notifies you through the [Microsoft AI at Work Roadmap](https://www.microsoft.com/microsoft-365/roadmap), formerly known as Microsoft 365 Roadmap. Before rollout, Microsoft notifies you through the [Microsoft 365 Message center](https://go.microsoft.com/fwlink/p/?linkid=2070717).

### What qualifies as a major update

Major updates are communicated at least 30 days in advance when an action is required and might include:

- User impacting changes to daily productivity such as changing a user's inbox, meetings, delegations, sharing and access that might result in help desk calls, or organizational conformance concerns.
- Changes to the themes, web parts, deployed Copilot agents, and other components that might impact customer customizations.
- Increases or decreases to visible capacity such as storage, number of rules, Copilot agents and prompts, items, or durations.
- Rebranding that might cause end-user confusion or result in help desk changes, collateral changes, or URL changes if the new URL isn't \*.cloud.microsoft
- A new service or application deployed with default settings turned on.
- Changes to where data is stored or accessed.

Note

If your organization is using targeted release for other Microsoft 365 services, you can continue to do so as we drive towards our converged release strategy. We recommend configuring release preferences for frontier, standard, and deferred audiences to align with the new release model as Microsoft begins delivering an increasing number of major updates through it over time. Use the Microsoft Message Center to keep up with new products and services using this audience-based release model.

For more information about targeted release for other Microsoft 365 services, see [Configure standard and targeted release](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide).

## Prerequisites

To configure standard and deferred release options, you need one of the following roles in the Microsoft 365 admin center:

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

- Enroll your organization in standard release to get the latest Microsoft 365 improvements as soon as they reach general availability. Optionally, assign business-critical users to deferred release to give them more time to prepare for major changes.
- Use deferred release if you need extra time to validate deferred-capable features before broad rollout. Assign a subset of IT pros or power users to standard release to evaluate new features for privacy and compliance readiness.
- Plan release phases around user impact and readiness, not individual feature controls, to help manage risk and set clear expectations for users.
- Align your release configuration with your change management and support readiness, including documentation, training, and help desk preparation.
- Review and adjust audience assignments over time as your organization's readiness and change tolerance evolve.

## Configure release options in Microsoft 365 admin center

By default, use standard release for Microsoft 365 service updates. This option meets the needs of most customers. To better manage your organization's readiness and testing needs, you can change the default release selection at any time in the Microsoft 365 admin center. It can take up to 24 hours for the following changes to take effect in Microsoft 365.

Note

Currently, the deferred release option only supports Microsoft Copilot-related features. For information on which features are deferred-capable, check Message Center posts. Microsoft will update this documentation as more features are supported.

To assign users or [security groups](https://learn.microsoft.com/en-us/entra/fundamentals/concept-learn-about-groups) to the deferred release audience, follow these steps:

1. Sign in to the Microsoft 365 admin center.
2. In the left navigation, expand **Copilot** and select **Settings**.

   [![Screenshot of Copilot settings in Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/copilot-settings-admin-center.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/copilot-settings-admin-center-expanded.png?view=o365-worldwide#lightbox)
3. Under the **All Settings** tab, select **Copilot release preferences: General Availability**.
4. Choose either **Standard Release** or **Deferred Release**.
5. Add any user or security group exceptions. You can add up to 100 exceptions to standard release or deferred release. Each user in a security group and each user added individually count toward the 100-user limit.

   - If you want to assign only a specific user or security group to deferred release, select **Standard Release**, search for the user or group, and select their name.

     ![Screenshot of standard release in Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/audience-release-options-standard.png?view=o365-worldwide)
   - If you want to assign only a specific user or security group to standard release, select **Deferred Release**, search for the user or group, and select their name.

6. Select **Save**.

Note

If you move users from standard release to deferred release, they might lose access to features that aren't available yet in deferred release.

## Related articles

[Modern change management for Microsoft 365 - Overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/plan-for-change-management?view=o365-worldwide)

[Get started with the Microsoft Release Communications MCP Server](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/mrc-mcp?view=o365-worldwide)

[Overview of Microsoft MCP Server for Enterprise](https://learn.microsoft.com/en-us/graph/mcp-server/overview)

[Get started with Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide)

[What's new in Message center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/message-center-updates?view=o365-worldwide)

[Set up the standard or targeted release options for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide)
