<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/auto-investigation-action-center -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Visit the Action center to see remediation actions

This article explains how to use the Action center in Microsoft Defender for Endpoint to review pending and completed remediation actions, approve actions when required, and understand action status.

During and after an automated investigation, remediation actions for threat detections are identified. Depending on the particular threat and how [automated investigation and remediation capabilities are configured](https://learn.microsoft.com/en-us/defender-endpoint/configure-automated-investigations-remediation) for your organization, some remediation actions are taken automatically, and others require approval. If you're part of your organization's security operations team, you can view pending and completed [remediation actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation#remediation-actions) in the **Action center**.

## Overview of the unified Action center

Recently, the Action center was updated. You now have a unified Action center experience. To access your Action center, go to the [Action center in the Microsoft Defender portal](https://security.microsoft.com/action-center) and sign in.

[![The Action center page in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-action-center-unified.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-action-center-unified.png#lightbox)

### What's changed?

The following table compares the new, unified Action center to the previous Action center.

| The new, unified Action center | The previous Action center |
| --- | --- |
| Lists pending and completed actions for devices and email in one location  <br>\([Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) plus [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) | Lists pending and completed actions for devices  <br>\([Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) only\) |
| Is located at:  <br>[Microsoft Defender Action center](https://security.microsoft.com/action-center) | Is located at:  <br>[Previous Action center portal](https://securitycenter.windows.com/action-center) |
| In the [Microsoft Defender portal](https://security.microsoft.com), choose **Action center**.<br><br>[![The navigation pane to the Action Center in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/media/action-center-nav-new.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/action-center-nav-new.png#lightbox) | In the Microsoft Defender portal, choose **Automated investigations** > **Action center**.<br><br>[![An older version of the navigation pane to the Action Center in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/media/action-center-nav-old.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/action-center-nav-old.png#lightbox) |

The unified Action center brings together remediation actions across Defender for Endpoint and Defender for Office 365. It defines a common language for all remediation actions, and provides a unified investigation experience.

You can use the unified Action center if you have appropriate permissions and one or more of the following subscriptions:

- [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about)
- [Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview)

## Use the Action center

To get to the unified Action center in the improved Microsoft Defender portal:

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, select **Action center**.
3. Use the **Pending actions** and **History** tabs. The following table summarizes what you'll see on each tab:
   | Tab | Description |
   | --- | --- |
   | **Pending** | Displays a list of actions that require attention. You can approve or reject actions one at a time, or select multiple actions if they have the same type of action \(such as **Quarantine file**\).<br><br>**TIP**: Make sure to [review and approve \(or reject\) pending actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation) as soon as possible so that your automated investigations can complete in a timely manner. |
   | **History** | Serves as an audit log for actions that were taken, such as:<br><br>- Remediation actions that were taken as a result of automated investigations<br>- Remediation actions that were approved by your security operations team<br>- Commands that were run and remediation actions that were applied during Live Response sessions<br>- Remediation actions that were taken by threat protection features in Microsoft Defender Antivirus<br><br>Provides a way to undo certain actions \(see [Undo completed actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation#undo-completed-actions)\). |
4. To customize, sort, filter, and export data in the Action center, take one or more of the following steps:

   [![The Action center with Columns and filters](https://learn.microsoft.com/en-us/defender-endpoint/media/new-action-center-columnsfilters.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/new-action-center-columnsfilters.png#lightbox)

   - Select a column heading to sort items in ascending or descending order.
   - Use the time period filter to view data for the past day, week, 30 days, or 6 months.
   - Choose the columns that you want to view.
   - Specify how many items to include on each page of data.
   - Use filters to view just the items you want to see.
   - Select **Export** to export results to a .csv file.

## Related content

For more information, see the following resources:

- [View and approve remediation actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation)
- [See the interactive guide: Investigate and remediate threats with Microsoft Defender for Endpoint](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Address false positives/negatives in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives)
