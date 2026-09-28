<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# Discovery setting for AI experiences enabled by usage-based billing

Important

The **AI experiences enabled by usage-based billing** setting is deprecated. This setting will be replaced by a new setting that allows admins to control whether users or groups can request access to experiences that require usage-based billing.

The **AI experiences enabled by usage-based billing** setting controls whether users in your organization can see AI experiences that rely on usage-based billing.

This setting provides a central discovery control. Turn it on to promote adoption and awareness of AI experiences. Keep it off to limit exposure until billing and governance are fully set up.

In short, this setting controls visibility, while Cost Management under the Copilot node in the Microsoft 365 admin center controls access and spending. Usage-based billing setup overrides discovery for the specified users that you enable usage-based billing for.

When enabled:

- Users can discover AI experiences \(for example, Copilot-powered agents and services like Copilot Cowork\) across Microsoft 365.
- To use these experiences, administrators must complete setup in **Copilot > Cost management**, including configuring billing and spending policies. For more information, see [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

After the setting is not selected:

- Usage-based AI experiences remain hidden from users, unless you set up usage-based billing for the user.

## Before you begin

To configure the setting in the Microsoft 365 admin center, you need to be assigned to the Global or the AI administrator role.

Important

Use roles with the fewest permissions. Lower permissioned accounts help improve security for your organization. Global Administrator is a highly privileged role. Limit its use to emergency scenarios when you can't use an existing role. For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Turn on the setting

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. Go to **Copilot** > **Settings** > **AI experiences enabled by usage-based billing**.
3. In the side panel, select the checkbox **Allow users to discover and use AI experiences enabled by usage-based billing in Microsoft Copilot**.

## Related articles

- [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits)
- [Usage-Based Billing and Cost Management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
- [Cowork Usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/cowork-usage-report)
