<!-- Source: https://learn.microsoft.com/en-us/intune/governance/monitor-audit-logs -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Use audit logs to track and monitor events in Microsoft Intune

In Microsoft Intune, there are audit logs that include a record of activities that generate a change. For example, the create, update \(edit\), delete, assign, and remote actions all create audit events.

Administrators can review the audit logs to track and monitor events for most Intune workloads. Auditing is enabled for all customers. It can't be disabled.

## Who can access the data?

Users with the following permissions can review audit logs:

- [Intune Administrator Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)
- Administrators assigned to an Intune role with **Audit data** - **Read** permissions. For a list of built-in Intune roles that have this permission, go to [Built-in role permissions for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles).

## View the audit logs

You can review audit logs in the monitoring group for each Intune workload, like compliance or Conditional Access.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** > **Audit logs**.
3. A list of the logs is shown. Select a log from the list to see the activity details.
4. If there are many logs, you can:

   1. Select **Date** and enter a start and end date. This date range can show logs for the previous year, month, week, or day.

      ![Filter audit logs by date in Microsoft Intune and Intune admin center.](https://learn.microsoft.com/en-us/intune/governance/media/monitor-audit-logs/audit-logs-date-range.png)
   2. Select **Add filters** > **Category**. Select a category from the list, like **Compliance**, **Device**, or **Role**. Then, select **Apply**.
   3. Select **Add filters** > **Activity**. The available options depend on the **Category** you select. Then, select **Apply**.

      For example, if you select the **Compliance** category, your **Activity** filter options look similar to the following image:

      ![Filter audit logs by compliance category and select an activity in Microsoft Intune and Intune admin center.](https://learn.microsoft.com/en-us/intune/governance/media/monitor-audit-logs/audit-logs-compliance-category-activity-options.png)

For related information about audit logs, go to:

- [Data storage and processing in Intune](https://learn.microsoft.com/en-us/intune/privacy/data-handling/data-storage-processing)
- [Use audit logs throughout Intune](https://learn.microsoft.com/en-us/intune/governance/integrate-azure-monitor#use-audit-logs-throughout-intune)
- [Audit, export, or delete personal data in Intune](https://learn.microsoft.com/en-us/intune/privacy/personal-data/manage-data-requests)

## Route logs to Azure Monitor

Audit logs and operational logs can also be routed to [Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/overview). In the Intune admin center, select **Tenant administration** > **Audit logs** > **Export**:

![Export log data to Azure monitor by selecting Export data settings in Microsoft Intune and Intune admin center.](https://learn.microsoft.com/en-us/intune/governance/media/monitor-audit-logs/audit-logs-export-data-settings.png)

When you export, a `.csv` file is created and saved locally, possibly in `C:\Users\UserName\AppData\Local\Temp\MicrosoftEdgeDownloads\GUID`.

When looking at the `.csv` file:

- **Initiated by \(actor\)** includes information on who ran the task, and where it was run.

  For example, if you run the activity in Intune in the Azure portal, then **Application** always lists **Microsoft Intune portal extension**, and the **Application ID** always uses the same GUID.
- The **Target\(s\)** section lists multiple targets and the properties that were changed.

For more information about this feature, including the prerequisites, go to [send log data to storage, event hubs, or log analytics](https://learn.microsoft.com/en-us/intune/governance/integrate-azure-monitor).

## Use Graph API to retrieve audit events

You can also use Graph API to get two years of audit events. For more information, go to [List auditEvents](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-list).

## Related articles

- [Send log data to storage, event hubs, or log analytics](https://learn.microsoft.com/en-us/intune/governance/integrate-azure-monitor)
- [Review client app protection logs](https://learn.microsoft.com/en-us/intune/app-management/protection/troubleshoot-protection-logs)
