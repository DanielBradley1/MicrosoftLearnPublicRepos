<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/siem-defender-workbooks -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Update workbooks to use Advanced Hunting data

Workbooks can query Microsoft Defender XDR data directly by using Advanced Hunting, without requiring the same data to be ingested into a workspace.

You can update existing workbooks to use Advanced Hunting data or create new workbooks that query Microsoft Defender XDR data directly.

## Prerequisites

Before you begin, make sure you have:

- Your tenant is [eligible for ISOC](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).
- To create and edit workbooks, either the **Workbooks** Unified RBAC permission with **Manage** access or the **Security Administrator** role.
- Access to the scopes and workloads used by the workbook queries.

Workbook permissions don't grant access to the underlying data. Data access and scoping are enforced when the query runs.

For example, a user can open a workbook that contains Defender for Endpoint data, but the workbook tile returns an error if the user doesn't have access to that data.

For more information, see [Update permissions and roles with Unified RBAC](https://learn.microsoft.com/en-us/azure/sentinel/transition-unified-rbac).

## Create a workbook using Advanced Hunting data

The **Workbooks** page includes example workbooks that use Microsoft Defender XDR data.

To create your own workbook:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Workbooks**.
3. Select **+ Add workbook**.
4. Select **Edit**.
5. In the query section, select **Advanced Hunting** as the data source.
6. Add or update the query for the workbook tile.
7. Save the workbook.

## Update an existing workbook

When you stop ingesting a supported Microsoft Defender XDR table into a workspace, update any workbooks that query that table.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Workbooks** and open the workbook you want to update.
3. Select **Edit**.
4. Change the query data source to **Advanced Hunting**.
5. Review the query and confirm that the table names are available in Advanced Hunting. Most table names remain the same.
6. Update any table or column references that differ in the Advanced Hunting schema.
7. Validate the workbook tiles, filters, and parameters.

For information about schema and data-type differences, see [Update Microsoft Sentinel content to use Advanced Hunting tables](https://learn.microsoft.com/en-us/azure/sentinel/transition-advanced-hunting-tables).

## Work with workbooks across workspaces

When one or more workspaces are connected, the **Workbooks** page includes a **Workspace** column that shows where each workbook is saved.

- A workspace name indicates that the workbook is saved to that workspace.
- **None** indicates that the workbook is saved at the tenant level.

You can filter the workbook list by workspace directly from the **Workbooks** page.

When you save a workbook, choose whether to save it to a specific workspace or at the tenant level.
