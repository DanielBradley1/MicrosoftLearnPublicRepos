<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/custom-detection-manage -->
<!-- Sitemap-Last-Modified: 2026-10-04 -->

# Manage existing custom detection rules

This article explains how to view, edit, run, enable, disable, and delete custom detection rules built from advanced hunting queries in Microsoft Defender XDR. You can also review triggered alerts and response actions for each rule.

## Available management actions for custom detection rules

You can view the list of existing custom detection rules, check their previous runs, and review the alerts that were triggered. You can also run a rule on demand, modify it, or create a new custom detection rule directly from the list.

Tip

Alerts raised by custom detections are available over alerts and incident APIs. For more information, see [Supported Microsoft Defender APIs](https://learn.microsoft.com/en-us/defender-xdr/api-supported).

For users who have onboarded a Microsoft Sentinel workspace to the unified Microsoft Defender portal, the custom detection rules list includes [analytics rules](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-defender-use-custom-rules#analytics-rules). The [View existing rules](#view-existing-rules) and [View rule details, modify rule, and run rule](#view-rule-details-modify-rule-and-run-rule) sections also apply to analytics rules unless otherwise indicated.

## View existing rules

To view your existing custom detection rules and analytics rules, navigate to **Hunting** > **Custom detection rules**.

[![Screenshot of the Custom detection rules page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/custom-detection-manage/unified-custom-det-list-tb.png)](https://learn.microsoft.com/en-us/defender-xdr/media/custom-detection-manage/unified-custom-det-list.png#lightbox)

To create a new custom detection rule directly from the **Custom detection rules** page, select **+ Create detection rule**. Selecting **+ Create detection rule** opens the custom detection rule wizard where you can define the query, alert details, and response actions. For more information, see [Create custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules).

You can filter for any column by going to **Add filter**, selecting the columns you want to filter for, and selecting **Add**. For each of the chosen columns, select the corresponding pill beside **Filters:**, select the columns, then **Apply**.

To search for specific rules, go to the search box in the upper right of the page and enter the name or rule ID of the rule you are looking for.

For multiworkspace organizations that onboarded multiple workspaces to Microsoft Defender, you can filter for workspaces using the columns **Workspace ID** or **Workspace name**.

The page lists all the rules with the following run information:

- **Last run** - When a rule was last run to check for query matches and generate alerts
- **Last run status** - Whether a rule ran successfully \(for custom detection rules only\)
- **Next run** - The next scheduled run
- **Status** - Whether a rule has been turned on or off

## View rule details, modify rule, and run rule

To view comprehensive information about a custom detection rule or an analytics rule, go to **Hunting** > **Custom detection rules** and then select the name of rule. You can then view general information about the rule, including information, its run status, and scope. The page also provides the list of triggered alerts and actions.

[![Screenshot of the Custom detection rule details page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/custom-detection-manage/custom-detect-rules-view.png)](https://learn.microsoft.com/en-us/defender-xdr/media/custom-detection-manage/custom-detect-rules-view.png#lightbox)

You can also take the following actions on the rule from the rule details page:

- **Open detection rule page** - opens the detection rule page to view triggered alerts and review actions \(for custom detection rules only\)
- **Run** - runs the rule immediately; this also resets the interval for the next run \(for custom detection rules only\)
- **Edit** - opens the rule wizard where you can modify the rule settings and the query
- **Modify query** - opens the query directly in advanced hunting for editing
- **Turn on** / **Turn off** - allows you to enable the rule or stop it from running
- **Delete** - turns off the rule and permanently removes it
- **Include or exclude from correlation** - allows you to include or exclude an analytics rule from correlation. See [Manage analytics rule correlation settings in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/exclude-analytics-rules-correlation) for more information.

### View and manage triggered alerts

In the rule details screen \(**Hunting** > **Custom detections** > **\[Rule name\]**\), go to **Triggered alerts**, which lists the alerts generated by matches to the rule. Select an alert to view detailed information about it and take the following actions:

- Manage the alert by setting its status and classification \(true or false alert\)
- Link the alert to an incident
- Run the query that triggered the alert on advanced hunting

### Review actions

In the rule details screen \(**Hunting** > **Custom detections** > **\[Rule name\]**\), go to **Triggered actions**, which lists the actions taken based on matches to the rule.

Tip

To quickly view information and take action on an item in a table, use the selection column \[✓\] at the left of the table.

## Related content

- [Custom detections overview](https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the advanced hunting query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Migrate advanced hunting queries from Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-migrate-from-mde)
- [Microsoft Graph security API for custom detections](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview?view=graph-rest-beta&preserve-view=true#custom-detections)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
