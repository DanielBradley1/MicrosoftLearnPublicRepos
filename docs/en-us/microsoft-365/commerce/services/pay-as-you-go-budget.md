<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-budget?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-02-02 -->

# Create a budget for pay-as-you-go billing in the Microsoft 365 admin center

This article explains how to set spending limits for pay-as-you-go billing. This feature helps you monitor usage, receive alerts as costs approach budget thresholds, and plan more effectively.

You can only set budgets at the billing policy level, not for individual users, agents, or sites. This policy means any limits or alerts apply to all services and users under the policy.

## Before you begin

To access the Microsoft 365 admin center, you must have one of the following roles:

- [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)
- [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?#ai-administrator)
- [Global Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader)

  Note

  Users with the [Global Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader) role can view billing policies and budgets, but they can't view spending data.

Caution

Global Administrators have almost unlimited access to your organization's settings and most of its data. To help keep your organization secure, we recommend that you limit the number of Global Administrators as much as possible.

## Create a budget

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. Go to **Copilot** > **Billing & usage**.
3. On the **Billing policies** tab, select the policy you want to manage.
4. In the policy panel, select the **Budget** tab.
5. To view current expenses for services linked to the policy, select **Spending**. Consumption data can take up to four hours to appear in the graph.
6. To configure your budget and alert preferences, select **Settings**, and set the following settings:

   a. Select the **Set limits for this billing policy** checkbox.  
   b. Under **Budget**, enter the dollar amount for your spending limit.  
   c. Under **Reset the budget**, select when you want to reset the budget.

   - Monthly \(resets on the first day of each month\)
   - Quarterly \(resets on January 1, April 1, July 1, and October 1\)
   - Yearly \(resets on January 1\)


   d. Under **Send email alerts** \(optional\):


   - Add recipients \(only [mail-enabled security groups](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group) are currently supported\).
   - Set the budget percentage that triggers alerts.

     - If selected, 100% is enabled by default.
     - You can add up to four more thresholds \(1-99%\).


   Note


   Email alerts can be delayed by up to 24 hours. Azure currently sends alerts, but they will transition to the Microsoft 365 admin center in a future release.

7. To apply your budget settings, select **Save**.

Important

The only way to stop billing is to [Disconnect a pay-as-you-go service](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-copilot?view=o365-worldwide#disconnect-a-pay-as-you-go-service). Reaching 100% of your budget doesn't stop the service or billing.
