<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-access -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Determine access controls for Copilot Cowork

This article explains how an admin controls who can use Copilot Cowork, and how the settings that affect access fit together. Access is spread across a few controls in the Microsoft 365 admin center, so this page brings them into one place and states, in order, what determines whether a user can use Cowork.

Important

A spending policy is an access control, not only a budget. Any user in the scope of a spending policy that selects Cowork can use Cowork, regardless of how small the credit limit is. A policy with a limit of one credit still grants access. To keep a user out of Cowork, don't include them in any spending policy that selects Cowork.

## Decide who can access Cowork

Work through the following order to determine whether a specific user can use Cowork. Each step describes what the control does and what it does *not* do.

1. **Is the user in the scope of at least one spending policy that selects Cowork?**

   This is the access grant. In the Microsoft 365 admin center, select **Copilot** > **Cost Management** > **Configuration**, and check every spending policy. A user has access to Cowork when a policy's scope includes them \(directly through **All users**, or through a security group\) and that policy selects Cowork under **Select agents and services**. If no policy in scope selects Cowork, the user has no access. For how to author policies, see [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

   Note

   Setting a very low credit limit doesn't prevent access. A user can still open Cowork and start work until the limit is reached. If your intent is to prevent use, remove the user from the policy scope rather than lowering their limit.
2. **Is the discovery setting on?**

   The **AI experiences enabled by usage-based billing** setting controls visibility only, not access. It determines whether users can see Cowork across Microsoft 365. Usage-based billing setup overrides discovery for users covered by a policy: a user covered by a spending policy that selects Cowork has access even when discovery is off. For more information, see [Discovery setting for AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences).
3. **If the user is in more than one policy, which policy's limits apply?**

   Access is decided per service by whether *any* applicable policy selects that service. A more restrictive policy doesn't override a more permissive one. When a user is in multiple policies that select Cowork, the precedence rules only choose which limits apply — they don't decide whether access is granted. The order is highest per-user limit, then largest overall policy limit, then most recently created policy. See [Users in multiple policies](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits) for the full rules.
4. **Which models can the user see?**

   Tenant model settings control model *availability*, not access. Turning off the Anthropic model family changes which models appear in the user's picker. It doesn't change whether the user can use Cowork. These settings are tenant-wide, so you can't use them to grant a model to a subset of users. For more information, see [Choose a model for Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models).
5. **What happens when a user reaches their limit?**

   Credit limits are a spending safeguard, not a real-time access gate. Credit consumption and limit enforcement are evaluated asynchronously, so a user might be able to start one or more tasks after their limit is reached before enforcement takes effect. To control access, use policy scope rather than the credit limit.

## Worked example: two overlapping policies

Consider a tenant with two spending policies that both select Cowork:

| Policy | Scope | Per-user limit | Selects Cowork? |
| --- | --- | --- | --- |
| Pilot policy | Security group of pilot users | 5,000 credits | Yes |
| Tenant budget policy | All users | 1 credit | Yes |

Because both policies select Cowork and their combined scope includes every user, **every user in the tenant has access to Cowork**. The 1-credit tenant policy is an access grant to the whole tenant, not a way to keep most users out. Pilot users belong to both policies; the precedence rules assign them the higher 5,000-credit limit, but that only sets their limit, not their access. To limit Cowork to the pilot group, remove Cowork from the tenant budget policy, or don't include non-pilot users in any policy that selects Cowork.

## Related content

- [Manage Copilot Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Choose a model for Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models)
- [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits)
- [Discovery setting for AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences)
- [Gain visibility into how users engage with Cowork in the Cowork Usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/cowork-usage-report)
