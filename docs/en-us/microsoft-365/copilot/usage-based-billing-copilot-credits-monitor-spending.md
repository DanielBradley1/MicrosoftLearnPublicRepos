<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending -->
<!-- Sitemap-Last-Modified: 2026-10-02 -->

# Monitor Copilot Credit spending

Use the **Overview** and **Consumption** tabs in the Cost Management dashboard to review Copilot Credit usage, funding sources, spending policies, users, groups, agents, and services.

## Overview tab

This dashboard provides a centralized view of spending patterns, helping administrators identify where credits are used, who consumes them, and how usage trends evolve over time.

The **Overview** tab refreshes every 4 hours.

As an administrator, use the Overview tab to:

- Review total Copilot Credit consumption.
- Compare usage-based billing including Copilot Credit Pre-purchase plans \(P3\) where applicable, with pay-as-you-go consumption. \(Side-by-side visibility\)
- Review consolidated spending insights across supported Copilot experiences.
- Understand Prepaid Capacity pack attribution across the Microsoft 365 admin center and Power Platform admin center.
- Identify changes in consumption patterns.
- Review policies or users that are approaching their spending limits.
- Access common actions for managing credit requests and spending policies.

The pay-as-you-go, and Prepaid Capacity pack breakdowns help organizations reconcile spending, understand funding sources, and evaluate usage across purchasing models.

Note

Use the Power Platform admin center for additional capacity allocation and workload-level details provided by that admin experience.

Note

Users can view their approximate Copilot Credit usage directly in Microsoft Copilot Cowork by entering `/cost`. This command shows the approximate cost in credits for the opened task so far, and additional credit usage details. For more information, see [Check your credit usage for Cowork tasks with `/cost`](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-cost).

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Copilot** > **Cost Management**.
2. Select the **Overview** tab.
3. Review these sections:

   - **Total Copilot Credits used**. Review total consumption for the selected period.
   - **Prepaid Capacity pack credits usage** \(if applicable\). Select the card to view details of Prepaid Capacity pack consumption by service. The flyout shows credits consumed by Microsoft 365 services and Power Platform services, along with the assigned capacity value when available.
   - **Pay-as-you-go credit used** \(includes Copilot Credit Pre-purchase plan \(P3\) credits\). Select the card to view the month-to-date details and spending trend.
   - **Number of Active users of Copilot Credits**. Users who have consumed Copilot Credits during the reporting period.
   - **Prepaid Capacity pack attribution**: Review available breakdowns for usage associated with the Microsoft 365 admin center and Power Platform admin center.


   Note


   Prepaid Capacity pack consumption can include usage managed in both the Microsoft 365 admin center and Power Platform admin center. Use the Power Platform admin center for additional allocation and usage details for Power Platform services.

4. From the **Top Actions** section, you can **View requests** and **Manage spending policies** by being alerted of spending policies credit usage near limit or users credit usage near limit.

### Viewing and managing credit requests

To view and approve credit requests from end users, select **View requests**. The **Credit requests** page displays all pending and approved requests. End users in your organization can submit credit requests for first-time use or limit increases.

The **Credit requests** page helps administrators review and manage requests from end users who need access to to a supported Copilot service or need a higher spending limit. Each request can include information such as the requested service, license status, current policy, and whether the user is currently covered by a spending policy.

### Configure custom request policies

Organizations can create custom request policies for credit requests. Custom request policies let administrators define alternate approvers or redirect requests to the appropriate business owner or approval workflow. For example, you can route requests to an internal IT portal or a ServiceNow workflow instead of requiring the request to be approved in the Microsoft 365 admin center.

To configure a custom request policy:

1. On the **Credit requests** page, select **Request policies**.
2. Select **Add request policy**.
3. Choose whether the policy applies to all products and services or to a supported specific product or service. A service-specific request policy takes precedence over a policy for all products and services.

   - **All products and services**: The policy applies to all credit requests.
   - **Specific product or service**: The policy applies only to requests for the selected product or service.

4. Enter the **redirect URL** and the **message** that end users see when they attempt to submit a request.
5. Optionally, add a Learn more link and identify the external service used to handle requests.
6. **Save** the request policy.

Requests submitted when a custom request policy applies still appear in the **All requests** view for audit and history. These requests are labeled **Handled externally**. Requests that don't match a custom request policy continue through the Microsoft credit request service and can be resolved in the Microsoft 365 admin center.

For a request labeled **Handled externally**, an administrator can still approve, reject, or mark the request as already processed. The label indicates that the request was routed to the organization's external workflow; it doesn't provide the approval result from that external system.

Each request shows key details like the requested app, license status, and current policy, making it easy to identify users who are blocked \(for example, 'Not in a policy'\) or need higher limits.

Administrators can act on requests by:

- Adding users to a spending policy to grant access and apply limits.
- Creating new policies or groups to onboard teams at scale.
- Adjusting policy limits to accommodate increased demand.
- Exporting requests for triaging offline.

### Manage spending policies

1. If users, groups, or policies are nearing their spending limits, they appear in the **Top actions** section. Select **Manage spending policies** to update the limits or create a new policy for the affected users or groups.
2. Review consumption trends to see which groups, agents, services, and users consume the most or least credits over time. Use these trends to decide whether to update spending limits, adjust policies, or redistribute credits.

### Monitor usage across groups, users, and services

The dashboard surfaces key insights to help you quickly understand consumption.

1. Select the **Consumption** tab.

- **Group-level spending** View which groups use the most and least Copilot credits in the current period. This view helps you identify teams that drive usage and those that might need enablement or controls.
- **User-level spending** See which individual users consume the most credits, so you can detect high usage patterns or outliers. Group and user level spending might differ because users can belong to multiple groups and policies.
- **Agents and services consumption** Track which Copilot experiences, such as Copilot agents or APIs, drive the highest credit usage across your tenant.

Each of these views includes quick actions, such as **Manage group spending** or **Manage user spending**, so you can take action directly from the insights.

### Understand consumption trends

The **spending trend chart** provides a visual breakdown of Copilot credit usage over time, including:

- **Prepaid credits consumption** \(including consumption from Message/Capacity Packs\)
- **Pay-as-you-go usage** \(including credits from a Pre-Purchase Plan\)
- **Total cumulative consumption**

This chart helps you:

- Track how quickly credits are consumed
- Monitor shifts between prepaid and pay-as-you-go usage
- Identify spikes or steady growth in demand across days or weeks

## Consumption tab

The **Consumption** tab provides reporting experiences for copilot credit usage by:

- Spending policy
- User
- Group
- Agent
- Service

The **Consumption** tab reports users who consume credits, not all users assigned to a policy. As a result, the number of active users might differ from the number of enabled users.

The **Consumption** tab refreshes every 2 hours.

Note

Exported reports are generated as a point-in-time snapshot, while dashboard views continue to retrieve live data. For this reason, exported counts and dashboard counts might temporarily differ. The export process supports larger result sets through an asynchronous export job.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Copilot** > **Cost Management**.
2. Select the **Consumption** tab.
3. The Policies view is the default view when you open the **Consumption** tab. It aggregates consumption information by spending policy for the selected reporting period.

   Use the view to review the following information:

   - **Policy**: The spending policy name.
   - **Policy status**: Whether the spending policy is active or inactive.
   - **Scope**: The users and groups included in the policy.
   - **Active users**: The number of users in the policy who generated usage during the selected reporting period. This value doesn't include every user who is eligible to use the policy.
   - **Credit usage**: The number of Copilot Credits consumed against the policy during the selected reporting period.
   - **Current spending limit**: The policy's current configured spending limit. This value doesn't change when you select a historical reporting period.
   - **Limit utilization**: Credit usage divided by the current spending limit.
   - **Billing method**: The billing method configured for the policy.


   When you review a historical reporting period, limit utilization compares usage from that period with the policy's current spending limit. Consider this difference when you interpret historical utilization.


   Using the dedicated policy-level view, administrators can:


   - Analyze consumption by individual spending policy.
   - Understand how credits are distributed across governed groups.
   - Identify which policies drive the highest usage.
   - Improve policy optimization and governance decisions.

4. In the **Users** view, select a user. The details panel shows total credits used, daily credit usage, spending policy history, and credits spent by spending policy for the past month. Credits spent by spending policy can include the policy name, associated agents and services, applicable limit, and credits used.

   - Users in a group spending policy that exceed their per-user spending limit: If a running task exceeds the per-user limit, it can complete without interruption. The excess usage doesn't count toward the policy limit, isn't billed \(at Microsoft's sole discretion\), and doesn't appear as consumed credits in the Cost Management dashboards \(**Microsoft 365 admin center > Copilot > Cost Management**\).
   - When a user moves from one Entra ID group to another during a billing period, the new group's spending policy becomes effective for that user. Credits consumed before the move are retained for billing at a policy level but aren't tracked at a user level in the Consumption tab view. Only the current usage against the current spending policy is displayed at a user level in the Consumption tab view.

5. In the **Groups** view, review groups included in spending policies. Select a group to open the details panel and view daily usage, assigned policy, and monthly credit limit.
6. In the **Agents and services** view, review usage for supported services. For example, Cowork and Work IQ API. This view shows active users, credits used, and session count for each supported service.
7. Compare usage across users, groups, agents, and services to help adjust policies or redistribute credit budgets.

## Related articles

- [Understand usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
- [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup)
- [Manage AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits)
- [Usage-based-billing guidance for CSPs, partner-managed customers, and MACC](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-csp-partner-macc)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
