<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-agent-instances?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-20 -->

# Manage agent instances in Microsoft 365 admin center

Once an admin or AI admin activates an agent, requestor can create instances of that agent. The Microsoft 365 admin center provides a centralized view for managing these instances:

- **Agent Registry** - Navigate to **Agents** > **All agents** > **Registry**. You can view agents with the **AI teammate** tag. You'll also see the number of instances that have been created for the specific agent.
- **Agent Details flyout** - Select an agent to open a flyout panel that displays the agent details.
- **Instance details** - Select **See details** to display a detailed list of all instances created under that agent. From this screen, administrators can perform the following actions:

  - **Manage individual instances** - Access and update settings for each instance.
  - **Review security and compliance status** - Ensure every instance meets organizational standards.
  - **Apply and customize licenses** - Assign licenses and configure options at the instance level.

This streamlined experience helps administrators maintain control, compliance, and flexibility across all agent instances.

Important

Certain features are available within Microsoft 365 admin center based on services licensed in your subscription. To view your licensed subscriptions in the [Microsoft 365 admin center](https://admin.cloud.microsoft/), select **Billing** > **Licenses** > **Subscriptions**. For more information, see [Plans and licensing](https://learn.microsoft.com/en-us/microsoft-agent-365/overview#plans-and-licensing).

## Block agent instances

You can block or unblock agent instances for the entire organization using the same controls available for any other app in the Microsoft 365 admin center. Blocking an instance stops it and any actions it's performing.

To block or unblock an agent:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to **Agents** > **All Agents**.
2. Select an agent from the list. A panel opens.
3. Under the **Details** tab, select the **Instances** tab to see all instances created by that agent.
4. Select an instance and choose **Block**.

To restore functionality, the administrator can **Unblock** the instance at any time.

## Delete agent instances

Administrators and AI administrators can delete an instance from the Microsoft 365 admin center when it's no longer needed.

1. In the left navigation pane, select **Agents** > **All agents**.
2. Filter the list by setting **Agent template** to **Yes**, and then select the agent. A panel opens where you can see the **Instances** tab.
3. Select the **Instances** tab to see all instances created by that agent.
4. Select the instance you want to delete, then select **Delete**.
5. Confirm the deletion when prompted.
6. Notify the owner of the deletion.
7. Remove or reassign Microsoft 365 licenses tied to the instance.
8. After 30 days, all instance accounts and data are permanently deleted. Audit logs are kept.
9. Once deleted, the instance no longer appears in the list.
