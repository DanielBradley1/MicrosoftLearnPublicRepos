<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-cost -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# Credit usage for Microsoft Copilot Cowork tasks

Tasks in Microsoft Copilot Cowork are measured in credits. The number of credits you have available to use each month is set by your organization and referred to as your monthly credit limit. Understanding how many credits a task in Cowork costs can help you plan how best to use Cowork within your monthly credit limit.

You can type `/cost` in Cowork to see the approximate Copilot Credit usage for a task, how many credits you have used this month, and how many remain. This command helps you understand the credit consumption associated with specific prompts and workloads. It does not cost any credits to use `/cost`.

## What is `/cost`?

When you type `/cost` in Cowork, you see details about the approximate cost, in credits, of the open task so far and how much of your monthly credit limit remains. The number of credits listed for the task is an aggregate consumption total for all actions within the current chat session. It is not a line-by-line breakdown of every action and its exact cost.

Credit data reflects the total activity for that session so far. You can use `/cost` to see credit usage for a task at any time. This includes going back to a previous task and typing `/cost` to see how many credits it used. Credit limits reset at the start of the month \(00:00 UTC\), and your limit is set by your organization.

Note

`/cost` shows an approximation of your consumption based on activity logged to date. It is not an authoritative billing record. Credit limits are set and managed by your organization, and questions about your limits and usage should be directed to the person who manages licensing in your organization.

## Individual and group usage

When your organization sets your monthly usage limit, they may set that limit as part of a group usage plan. That means that while you may have an individual monthly credit limit, your limit may also be part of a larger group limit.

Depending on how your organization sets up your usage limits within a group, your available monthly credits might be affected by how other users in your group consume credits. For example, if you're on a group plan, your credits may be drawn from a shared monthly limit. Your usage could show credits remaining, but if the group has reached its overall limit, those credits might not be available.

Direct any questions about how your monthly credit limit is set up to the person in your organization who [manages credit limits and usage](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

## Important considerations for `/cost`

`/cost` is not intended for the following:

- **Official billing or invoice reconciliation**: `/cost` is an in-product estimate, not a source-of-truth billing ledger for invoices, chargebacks, or budget reconciliation. Use your organization's billing portal or contact your organization for official billing details.
- **Admin or tenant policy management**: You can request additional credits from the person in your organization who [manages credit limits and usage](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).
- **Historical usage analytics**: `/cost` shows your current billing cycle only. It does not provide month-over-month trends, usage history, or long-range forecasts.

## FAQs

### Why does my balance sometimes look lower than expected?

Usage data is near real time, but it might not immediately reflect actions you just completed. Depending on how your organization set up your credit limit, you may be part of a group usage plan where other people in your organization share a set of credits.

Questions about how your monthly credit limit is set up should be directed to the person in your organization who manages credit limits and usage.

### Do my credits carry over?

No. Credits reset monthly and do not carry over. Any unused credits from the previous month are not added to your credit limit for the new month.

### What if I run out of credits?

If you reach your credit limit, you can contact your organization to request more. Requests are sent to the person in your organization who manages licensing.

### Can I check the cost before running a task?

No. Currently, you can only use `/cost` to check how many credits a task has already used.

## Related resources

- [Copilot Credits licensing guide](https://aka.ms/CopilotCredits/LicensingGuide)
- [Copilot Cowork overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/index)
- [Usage-based billing setup guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup#getting-started-with-usage-based-billing)
- [Cost management in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits#understand-usage-based-billing-and-cost-management-for-copilot-credits)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
