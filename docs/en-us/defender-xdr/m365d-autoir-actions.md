<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-actions -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# View and manage actions in the Action center

Important

As of September 1, 2026, automated Investigation and Response \(AIR\) will no longer run as a separate investigation experience or be available for manual triggering in Microsoft Defender for Endpoint alerts and remediations.

- AIR detection and response capabilities for Defender for Endpoint are already included in Microsoft Defender for Endpoint's default antivirus protection stack and run automatically. For on-demand investigations, run a full antivirus scan as needed.
- This change applies only to Microsoft Defender for Endpoint. AIR capabilities for Defender for Office 365 remain available.

Threat protection features in Microsoft Defender XDR can result in certain remediation actions. Here are some examples:

- [Automated investigations](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir) can result in remediation actions that are taken automatically or await your approval.
- Antivirus, anti-malware, and other threat protection features can result in remediation actions, such as blocking a file, URL, or process, or sending an artifact to quarantine.
- Your security operations team can take remediation actions manually, such as during [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) or while investigating [alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts) or [incidents](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents).

Note

You must have [required permissions for Action center tasks](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center#required-permissions-for-action-center-tasks) to approve or reject remediation actions. For more information, see the [prerequisites for automated investigation and response](https://learn.microsoft.com/en-us/defender-xdr/m365d-configure-auto-investigation-response#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

To navigate to the Action center, take one of the following steps:

- Go to the [Microsoft Defender Action center](https://security.microsoft.com/action-center); or
- In the [Microsoft Defender portal](https://security.microsoft.com), in the Automated investigation & response card, select **Approve in Action Center**.

## Review pending actions in the Action center

It's important to approve \(or reject\) pending actions as soon as possible so that your automated investigations can proceed and complete in a timely manner.

1. Go to [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) and sign in.
2. In the navigation pane under Actions and submissions, choose **Action center**.
3. In the Action center, on the **Pending** tab, select an item in the list. The item's flyout pane opens. Here's an example.

   [![The options to approve or reject an action](https://learn.microsoft.com/en-us/defender-xdr/media/air-actioncenter-itemselected.png)](https://learn.microsoft.com/en-us/defender-xdr/media/air-actioncenter-itemselected.png#lightbox)
4. Review the information in the flyout pane, and then take one of the following steps:

   - Select **Open investigation page** to view more details about the investigation.
   - Select **Approve** to initiate a pending action.
   - Select **Reject** to prevent a pending action from being taken.
   - Select **Go hunt** to go into [Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

Tip

You now have more options to review and approve/reject a remediation action. In addition to using the Action center, you can also approve or reject a remediation action while reviewing an incident. For more information, see [Approve or reject remediation actions](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#approve-or-reject-remediation-actions).

## Undo completed actions

If you determine that a device or a file isn't a threat, you can undo the remediation actions that were taken. You can undo actions whether they were taken automatically or manually. In the Action center, on the **History** tab, you can undo any of the following actions:

| Action source | Supported Actions |
| :--- | :--- |
| - Automated investigation  <br>- Microsoft Defender Antivirus  <br>- Manual response actions | - Isolate device  <br>- Contain device  <br>- Contain user  <br>- Restrict code execution  <br>- Quarantine a file  <br>- Remove a registry key  <br>- Stop a service  <br>- Disable a driver  <br>- Remove a scheduled task |

Note

Only Security Administrators and higher are allowed access to undo operations such as File Quarantine.

### Undo one remediation action

To undo a single remediation action:

1. Go to the [Microsoft Defender Action center](https://security.microsoft.com/action-center) and sign in.
2. On the **History** tab, select an action that you want to undo.
3. In the pane on the right side of the screen, select **Undo**.

### Undo multiple remediation actions

To undo multiple remediation actions at once:

1. Go to the [Microsoft Defender Action center](https://security.microsoft.com/action-center) and sign in.
2. On the **History** tab, select the actions that you want to undo. Make sure to select items that have the same Action type. A flyout pane opens.
3. In the flyout pane, select **Undo**.

### Remove a file from quarantine across multiple devices

To remove a quarantined file from multiple devices at once, perform the following steps:

1. Go to the Action center \([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)\) and sign in.
2. On the **History** tab, select a file that has a **Quarantine file** Action type.
3. In the pane on the right side of the screen, select **Apply to X more instances of the selected quarantined file**, and then select **Undo**.

## Next steps

- [View the details and results of an automated investigation](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-results)
- [Address false positives or false negatives](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-report-false-positives-negatives)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
