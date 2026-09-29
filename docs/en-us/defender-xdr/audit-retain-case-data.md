<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/audit-retain-case-data -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Audit and retain case data in Log Analytics \(preview\)

Case management activity from the Microsoft Defender portal is automatically synced to the `SecurityCaseEvent` table in Log Analytics when your tenant has a connected primary Microsoft Sentinel workspace. You can use KQL to review case activity, investigate changes, create visualizations and dashboards, and retain case history beyond the default 180-day retention period in Defender.

Case audit and retention supports incident cases and all other supported case types. It syncs case activity and changes to related case items, including:

- Cases
- Case tasks
- Case comments
- Case attachments
- Case relations

Note

For attachments, only attachment metadata is exported. Attachment contents aren't exported.

Each change is recorded as an event in the `SecurityCaseEvent` table. Events can include create, update, delete, link, and unlink operations.

## Prerequisites

To access case audit and retention data, you need read access to the Log Analytics workspace to query case data.

For more information, see [Manage access to Log Analytics workspaces](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/manage-access).

## How case data is synced

Case data is automatically synced to the `SecurityCaseEvent` table in your current primary Microsoft Sentinel workspace. You don't need to enable case sync in Defender settings, and case sync can't be turned off.

If you change the primary Microsoft Sentinel workspace, case activity automatically begins flowing to the new primary workspace. The change can take up to 15 minutes to take effect.

## Query case activity

You can query case activity by using the `SecurityCaseEvent` table in Advanced hunting in the Microsoft Defender portal, Microsoft Sentinel, or Log Analytics. Use KQL to review case changes, investigate activity, create visualizations, and build dashboards.

For the full table schema, see [SecurityCaseEvent](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/securitycaseevent).

If you're new to querying data in Log Analytics, see [Log Analytics tutorial](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-tutorial).

### Audit cases using example queries in the Azure portal

Example queries are available for case audit and retention. You can run the queries as-is, or modify them for your investigation, reporting, auditing, or dashboard needs.

Example queries include:

- Recent changes on a case
- Cases by status
- Cases with most open tasks
- Inactive cases
- Urgent open cases
- Cases with overdue tasks
- Case tasks created daily
- All case management activity by a specific user
- Cases and tasks assigned to a specific user
- Users with most open case tasks
- Full cases snapshot
- Single case snapshot
- Point-in-time single case snapshot
- Cases by SLA status

To use an example query:

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Open your Microsoft Sentinel workspace.
3. Select **Logs**.
4. Select **Queries hub**.
5. Select **Add filter**.
6. Filter by **Resource type: Case Management**.

   [![Screenshot of the Queries hub filtered by Case Management resource type and Audit category.](https://learn.microsoft.com/en-us/defender-xdr/media/audit-retain-case-data/queries-hub-case-management.png)](https://learn.microsoft.com/en-us/defender-xdr/media/audit-retain-case-data/queries-hub-case-management.png#lightbox)
7. Hover over an example query.
8. Select **Run** to run the query as-is, or select **Load to editor** to customize the query before selecting **Run**.

   Note

   Some queries include placeholders, such as a case ID, user, or status value. To update placeholder values before running the query, select **Load to editor**.

   Tip

   To edit a query after results appear, select **User Query** to return to the query editor.

### Audit cases using example queries in the Microsoft Defender portal

The same example queries available for case audit and retention in the Azure portal are also available in Advanced hunting in the Microsoft Defender portal.

To access the example queries:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Investigation & response** > **Hunting** > **Advanced hunting**.
3. Select **Queries** from the dropdown.
4. Expand **Community queries** > **Microsoft Sentinel**. The case management example queries are listed there.

   [![Screenshot of Advanced hunting in the Microsoft Defender portal showing case management example queries under Community queries and Microsoft Sentinel.](https://learn.microsoft.com/en-us/defender-xdr/media/audit-retain-case-data/advanced-hunting-case-management-queries.png)](https://learn.microsoft.com/en-us/defender-xdr/media/audit-retain-case-data/advanced-hunting-case-management-queries.png#lightbox)

## Manage retention

After case data is synced to Log Analytics, retention is controlled by the retention settings for the `SecurityCaseEvent` table and its Log Analytics workspace.

You can manage table retention directly in the Microsoft Defender portal:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Go to **Microsoft Sentinel** > **Configuration** > **Tables**.
3. If needed, select the Microsoft Sentinel workspace that contains the `SecurityCaseEvent` table.
4. Select the `SecurityCaseEvent` table.
5. Select **Manage table**.
6. Configure the analytics and total retention settings.
7. Review any warnings or messages about the effects of the changes.
8. Select **Save**.

The **Tables** page also provides Table insights to help you review ingestion volume, when data was last received, estimated daily ingestion costs, and unusual changes in ingestion before you modify table retention or tier settings.

For more information, see:

- [Configure table settings in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/manage-table-tiers-retention)
- [Manage data tiers and retention in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/manage-data-overview#how-data-tiers-and-retention-work)
- [Plan costs and understand pricing and billing for Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/billing?tabs=simplified%2Ccommitment-tiers)

## Related content

- [Case management in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management)
- [SecurityCaseEvent](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/securitycaseevent)
- [Log Analytics tutorial](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-tutorial)
- [Configure table settings in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/manage-table-tiers-retention)
- [Manage data tiers and retention in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/manage-data-overview#how-data-tiers-and-retention-work)
- [Plan costs and understand pricing and billing for Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/billing?tabs=simplified%2Ccommitment-tiers)
