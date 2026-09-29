<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-results -->
<!-- Sitemap-Last-Modified: 2025-04-28 -->

# Details and results of an automated investigation

Important

As of September 1, 2026, automated Investigation and Response \(AIR\) will no longer run as a separate investigation experience or be available for manual triggering in Microsoft Defender for Endpoint alerts and remediations.

- AIR detection and response capabilities for Defender for Endpoint are already included in Microsoft Defender for Endpoint's default antivirus protection stack and run automatically. For on-demand investigations, run a full antivirus scan as needed.
- This change applies only to Microsoft Defender for Endpoint. AIR capabilities for Defender for Office 365 remain available.

With Microsoft Defender XDR, when an [automated investigation](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir) runs, details about that investigation are available both during and after the automated investigation process. If you have the [necessary permissions](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center#required-permissions-for-action-center-tasks), you can view those details in an investigation details view that provides you with up-to-date status and the ability to approve any pending actions.

## Unified investigation page

The investigation page includes information across your devices, email, and collaboration content. The unified investigation page defines a common language and provides a unified experience for automatic investigations across [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) and [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about). To access the unified investigation page, select the link in the yellow banner you'll see on:

- Any investigation page in the [Microsoft Purview portal](https://go.microsoft.com/fwlink/p/?linkid=2077149)
- Any investigation page in the Microsoft Defender portal \([https://security.microsoft.com](https://security.microsoft.com)\)
- Any incident or Action center experience in the [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139)

## Open the investigation details view

You can open the investigation details view by using one of the following methods:

- [Select an item in the Action center](#select-an-item-in-the-action-center)
- [Select an investigation from an incident details page](#open-an-investigation-from-an-incident-page)

### Select an item in the Action center

The [Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center) \([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)\) brings together [remediation actions](https://learn.microsoft.com/en-us/defender-xdr/m365d-remediation-actions) across your devices, email & collaboration content, and identities. Listed actions include remediation actions that were taken automatically or manually. In the Action center, you can view actions that are awaiting approval and actions that were already approved or completed. You can also navigate to more details, such as an investigation page.

Tip

You must have [certain permissions](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center#required-permissions-for-action-center-tasks) to approve, reject, or undo actions.

1. Go to [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) and sign in.
2. In the navigation pane, choose **Action center**.
3. On either the **Pending** or **History** tab, select an item. Its flyout pane opens.
4. Review the information in the flyout pane, and then take one of the following steps:

   - Select **Open investigation page** to view more details about the investigation.
   - Select **Approve** to initiate a pending action.
   - Select **Reject** to prevent a pending action from being taken.
   - Select **Go hunt** to go into [Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

### Open an investigation from an incident page

Use the incident page to view detailed information about an incident, including alerts that were triggered information about any affected devices, user accounts, or mailboxes.

1. Go to [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) and sign in.
2. In the navigation pane, choose **Incidents & alerts** > **Incidents**.
3. Select an item in the list, and then choose **Open incident page**.
4. Select the **Investigations** tab, and then select an investigation in the list. Its flyout pane opens.
5. Select **Open investigation page**.

## Investigation details

Use the investigation details view to see past, current, and pending activity pertaining to an investigation. Here's an example.

[![The investigation details page in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-autoir-results/mtp-air-investdetails.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-autoir-results/mtp-air-investdetails.png#lightbox)

In the Investigation details view, you can see information on the **Investigation graph**, **Alerts**, **Mailboxes**, **Devices**, **Users**, **Evidence**, **Entities**, **Log**, and **Pending actions** tabs, described in the following table.

Note

The specific tabs you see in an investigation details page depends on what your subscription includes. For example, if your subscription does not include Microsoft Defender for Office 365 Plan 2, you won't see a **Mailboxes** tab.

| Tab | Description |
| :--- | :--- |
| **Investigation graph** | Provides a visual representation of the investigation. Depicts entities and lists threats found, along with alerts and whether any actions are awaiting approval.  <br>You can select an item on the graph to view more details. For example, selecting the **Evidence** icon takes you to the **Evidence** tab, where you can see detected entities and their verdicts. |
| **Alerts** | Lists alerts associated with the investigation. Alerts can come from threat protection features on a user's device, in Office apps, Microsoft Defender for Cloud Apps, and other Microsoft Defender XDR features.  <br>  <br>If you see *Unsupported alert type*, it means that automated investigation capabilities cannot pick up that alert to run an automated investigation. However, you can [investigate these alerts manually](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#alerts). |
| **Devices** | Lists devices included in the investigation along with their remediation level. \(Remediation levels correspond to [the automation level for device groups](https://learn.microsoft.com/en-us/defender-xdr/m365d-configure-auto-investigation-response#review-or-change-the-automation-level-for-device-groups).\) |
| **Mailboxes** | Lists mailboxes that are impacted by detected threats. |
| **Users** | Lists user accounts that are impacted by detected threats. |
| **Evidence** | Lists pieces of evidence raised by alerts or investigations. Includes verdicts \(*Malicious*, *Suspicious*, *Unknown*, or *No threats found*\) and remediation status. |
| **Entities** | Provides details about each analyzed entity, including a verdict for each entity type \(*Malicious*, *Suspicious*, or *No threats found*\). |
| **Log** | Provides a chronological, detailed view of all the investigation actions taken after an alert was triggered. |
| **Pending actions history** | Lists items that require approval to proceed. Go to the Action center \([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)\) to approve pending actions. |

## Investigation states

The following table lists investigation states and what they indicate.

| Investigation state | Definition |
| --- | --- |
| Benign | Artifacts were investigated and a determination was made that no threats were found. |
| PendingResource | An automated investigation is paused because either a remediation action is pending approval, or the device on which an artifact was found is temporarily unavailable. |
| UnsupportedAlertType | An automated investigation is not available for this type of alert. Further investigation can be done manually, by using advanced hunting. |
| Failed | At least one investigation analyzer ran into a problem where it couldn't complete the investigation. If an investigation fails after remediation actions were approved, the remediation actions might still have succeeded. |
| Successfully remediated | An automated investigation completed, and all remediation actions were completed or approved. |

To provide more context about how investigation states show up, the following table lists alerts and their corresponding automated investigation state. This table is included as an example of what a security operations team might see in the Microsoft Defender portal.

| Alert name | Severity | Investigation state | Status | Category |
| --- | --- | --- | --- | --- |
| Malware was detected in a wim disk image file | Informational | Benign | Resolved | Malware |
| Malware was detected in a rar archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a rar archive file | Informational | UnsupportedAlertType | New | Malware |
| Malware was detected in a rar archive file | Informational | UnsupportedAlertType | New | Malware |
| Malware was detected in a rar archive file | Informational | UnsupportedAlertType | New | Malware |
| Malware was detected in a zip archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a zip archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a zip archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a zip archive file | Informational | PendingResource | New | Malware |
| Wpakill hacktool was prevented | Low | Failed | New | Malware |
| GendowsBatch hacktool was prevented | Low | Failed | New | Malware |
| Keygen hacktool was prevented | Low | Failed | New | Malware |
| Malware was detected in a zip archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a rar archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a rar archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a zip archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a rar archive file | Informational | PendingResource | New | Malware |
| Malware was detected in a rar archive file | Informational | PendingResource | New | Malware |
| Malware was detected in an iso disc image file | Informational | PendingResource | New | Malware |
| Malware was detected in an iso disc image file | Informational | PendingResource | New | Malware |
| Malware was detected in a pst outlook data file | Informational | UnsupportedAlertType | New | Malware |
| Malware was detected in a pst outlook data file | Informational | UnsupportedAlertType | New | Malware |
| MediaGet detected | Medium | PartiallyInvestigated | New | Malware |
| TrojanEmailFile | Medium | SuccessfullyRemediated | Resolved | Malware |
| CustomEnterpriseBlock malware was prevented | Informational | SuccessfullyRemediated | Resolved | Malware |
| An active CustomEnterpriseBlock malware was blocked | Low | SuccessfullyRemediated | Resolved | Malware |
| An active CustomEnterpriseBlock malware was blocked | Low | SuccessfullyRemediated | Resolved | Malware |
| An active CustomEnterpriseBlock malware was blocked | Low | SuccessfullyRemediated | Resolved | Malware |
| TrojanEmailFile | Medium | Benign | Resolved | Malware |
| CustomEnterpriseBlock malware was prevented | Informational | UnsupportedAlertType | New | Malware |
| CustomEnterpriseBlock malware was prevented | Informational | SuccessfullyRemediated | Resolved | Malware |
| TrojanEmailFile | Medium | SuccessfullyRemediated | Resolved | Malware |
| TrojanEmailFile | Medium | Benign | Resolved | Malware |
| An active CustomEnterpriseBlock malware was blocked | Low | PendingResource | New | Malware |

## Next steps

- [View and manage remediation actions](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-actions)
- [Learn more about remediation actions](https://learn.microsoft.com/en-us/defender-xdr/m365d-remediation-actions)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
