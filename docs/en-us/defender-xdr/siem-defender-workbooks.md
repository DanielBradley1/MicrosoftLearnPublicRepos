<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/siem-defender-workbooks -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Create and manage workbooks with ISOC in Microsoft Defender \(preview\)

Use workbooks with Integrated Security Operations Center \(ISOC\) in Microsoft Defender to create interactive dashboards that visualize and monitor security data by using advanced hunting queries.

Note

This feature is in preview. Capabilities and availability might change during the preview period.

## Prerequisites

Before you begin, make sure you have:

- Your tenant is [eligible for ISOC](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).
- To create and edit workbooks, either the **Workbooks** Unified RBAC permission with **Manage** access or the **Security Administrator** role.
- Access to the scopes and workloads used by the workbook queries.

## Explore example workbooks

Use the example workbooks to become familiar with the workbook experience and available visualizations.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Microsoft Sentinel** > **Workbooks**.
3. Under **Getting started**, select an example workbook.
4. Explore the workbook data and visualizations.

[![Screenshot showing example workbooks for device activity, email security, identity monitoring, and alerts and incidents.](https://learn.microsoft.com/en-us/defender-xdr/media/siem-defender-workbooks/getting-started-example-workbooks.png)](https://learn.microsoft.com/en-us/defender-xdr/media/siem-defender-workbooks/getting-started-example-workbooks.png#lightbox)

Example workbooks are provided for exploration. To build and save your own dashboard, [create a new workbook](#create-a-workbook).

## Create a workbook

Create a workbook that uses advanced hunting queries to visualize Defender XDR data.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Workbooks**.
3. Select **+ Add workbook**.
4. Select **Edit**.
5. Edit the existing query section or add a new query section.
6. For **Data source**, select **Advanced hunting**.
7. Enter an advanced hunting query.
8. Select **Run query** to review the query results.
9. Configure the query settings.

   Available settings include:

   - **Time range**
   - **Visualization**
   - **Size**
   - Visual formatting settings

10. Select **Apply changes**.
11. Add or edit other workbook sections as needed.

    You can add text, queries, and parameters.
12. When you're done, select **Done editing**.
13. Select **Save**.
14. Enter a title for the workbook.
15. Select **Save**.

The workbook is saved automatically at the tenant level.

## View saved workbooks

Saved workbooks appear on the **My workbooks** tab.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Workbooks**.
3. Select the **My workbooks** tab.
4. Use search or the available filters to find a workbook.
5. Select the workbook to view its details.
6. Select **View saved workbook**.

Saved workbooks are visible to users with the **Workbooks** permission with **Reader** access or the **Security Reader** role. The data displayed depends on the user's access to the relevant scope and workload.

## Edit a workbook

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Workbooks**.
3. On the **My workbooks** tab, select the workbook you want to update.
4. Select **View saved workbook**.
5. Select **Edit**.
6. Update the workbook sections, queries, parameters, or visualizations.
7. Select **Apply changes** after editing a section.
8. When you're done, select **Done editing**.
9. Select **Save**.

## Refresh workbook data

Refresh a workbook to display updated data.

In the workbook toolbar, select one of the following options:

- **Refresh** to manually refresh the workbook data.
- **Auto refresh** to refresh the workbook automatically at a configured interval.

Supported auto-refresh intervals range from 5 minutes to 1 day.

Auto refresh pauses while you're editing a workbook. The interval restarts when you return to view mode or manually refresh the workbook.

Auto refresh is turned off when you close the workbook. Turn it on again the next time you open the workbook, as needed.

## Delete a workbook

Warning

Deleting a workbook permanently removes the workbook and its customizations. This action can't be undone.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Workbooks**.
3. Select the **My workbooks** tab.
4. Select the workbook you want to remove.
5. Select **Delete**.
6. Select **Yes** to confirm.

## Related content

- [Create and edit workbooks with Copilot in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/defender-copilot-workbooks)
