<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/defender-copilot-workbooks -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Create and edit workbooks with Copilot for ISOC in Microsoft Defender \(preview\)

Use Copilot for Workbooks with Integrated Security Operations Center \(ISOC\) in Microsoft Defender to create and edit workbooks by using natural-language prompts. Describe the dashboard you want, and Copilot generates the KQL, panels, parameters, and layout.

You can review the generated workbook, refine it conversationally, and save the finished workbook. You can also use the Advanced Editor to manually update generated KQL.

## Prerequisites

Before you begin, make sure the following requirements are met:

- Your tenant is [eligible for ISOC](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).
- Microsoft Security Copilot is enabled for your tenant and has available Security Compute Units \(SCUs\).
- You have permission to create and save workbooks in Microsoft Defender.

Note

During this preview, Copilot for Workbooks supports Advanced Hunting tables as the data source. Log Analytics data isn't supported.

## Create a workbook with Copilot

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Workbooks**.
3. Select **Add Workbook**.
4. Select **Edit** > **Edit with Copilot**.

   [![Screenshot of the Copilot panel in a Microsoft Defender workbook showing example natural-language prompts for generating workbook content.](https://learn.microsoft.com/en-us/defender-xdr/media/defender-copilot-workbooks/copilot-workbooks-prompt-examples.png)](https://learn.microsoft.com/en-us/defender-xdr/media/defender-copilot-workbooks/copilot-workbooks-prompt-examples.png#lightbox)
5. In the Copilot panel, describe the dashboard you want to create.
6. Submit the prompt.

   Copilot generates a draft workbook on the canvas. The draft can include a descriptive header, parameters, and one or more visualizations.

   [![Screenshot of a Microsoft Defender workbook generated with Copilot showing an endpoint investigation dashboard with charts and the Copilot panel.](https://learn.microsoft.com/en-us/defender-xdr/media/defender-copilot-workbooks/copilot-workbooks-generated-dashboard.png)](https://learn.microsoft.com/en-us/defender-xdr/media/defender-copilot-workbooks/copilot-workbooks-generated-dashboard.png#lightbox)
7. Review the generated workbook.
8. Refine the workbook as needed.
9. Save the workbook.

## Refine a workbook with Copilot

After Copilot generates a workbook, continue the conversation to update specific parts of the workbook.

1. In the Copilot panel, describe the change you want to make.

   For example:

   - `Group by tenant.`
   - `Add a stat card with the total volume.`
   - `Turn this into a bar chart.`
   - `Filter to Windows devices only.`

2. Submit the prompt.

   Copilot updates the workbook based on your request.
3. Review the updated workbook.
4. Continue refining the workbook as needed.

Copilot updates the workbook as you continue the conversation.

## Review and undo workbook changes

Copilot automatically updates the workbook based on your prompts. You can use **Undo** or **Redo** as you refine the workbook.

| Action | Description |
| --- | --- |
| **Undo** | Reverts the most recent Copilot change. |
| **Redo** | Restores a change that you previously undid. |
| **Save** | Saves the workbook to your account. |
| **Advanced Editor** | Opens the workbook definition and KQL for manual editing. |

Tip

Make changes incrementally so that you can use **Undo** and **Redo** predictably as you refine the workbook.

## Edit generated KQL manually

You can manually edit Copilot-generated KQL by using the workbook Advanced Editor.

1. Open the workbook panel you want to modify.
2. Open the **Advanced Editor**.
3. Review the generated KQL.
4. Make the required changes.
5. Apply the changes to the workbook.

## Prompting tips

Use the following guidance when creating or refining a workbook:

- Describe the goal of the dashboard instead of providing only a query.
- Specify a time range, such as `last 24 hours` or `last 7 days`.
- Specify the visualization you want, such as a table, bar chart, time series, stat card, or map.
- Make changes in small steps and review each update before requesting another change.
- Mention the relevant Advanced Hunting table when you know which table contains the data.

For example:

> Dashboard of the top 10 signed-in users with failed sign-ins in the last 24 hours.

Or:

> Timeline of Defender for Endpoint alerts by severity, grouped by device.

## Troubleshoot Copilot for Workbooks

### Edit with Copilot isn't shown

1. Verify that Microsoft Security Copilot is provisioned for your tenant.
2. Verify that Security Compute Units are available.
3. Return to the Workbooks page.
4. Refresh the page.

### A generated workbook doesn't return results

1. Check the time-range parameter.
2. Increase the time range if needed.
3. Verify that the Advanced Hunting tables referenced by the generated query contain data for your tenant.
4. Run the underlying query in Advanced Hunting to verify that it returns results.
5. If needed, ask Copilot to explain why the panel is empty and suggest a correction.

### A visualization doesn't display the expected results

Describe the specific change you want Copilot to make.

For example:

- `Show only the top 10 results.`
- `Change this to a stacked bar chart.`
- `Group the results by day.`

If the change doesn't produce the expected result, use **Undo** to revert it.

## Related content

- [Create and manage workbooks with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-workbooks)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Microsoft Copilot in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-in-microsoft-365-defender)
