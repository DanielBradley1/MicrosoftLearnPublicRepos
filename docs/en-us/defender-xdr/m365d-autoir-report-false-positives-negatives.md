<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-report-false-positives-negatives -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Address false positives or false negatives in Microsoft Defender XDR

Important

As of September 1, 2026, automated Investigation and Response \(AIR\) will no longer run as a separate investigation experience or be available for manual triggering in Microsoft Defender for Endpoint alerts and remediations.

- AIR detection and response capabilities for Defender for Endpoint are already included in Microsoft Defender for Endpoint's default antivirus protection stack and run automatically. For on-demand investigations, run a full antivirus scan as needed.
- This change applies only to Microsoft Defender for Endpoint. AIR capabilities for Defender for Office 365 remain available.

False positives or negatives can occasionally occur with any threat protection solution. If [automated investigation and response capabilities](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir) in Microsoft Defender XDR missed or wrongly detected something, there are steps your security operations team can take:

- [Report a false positive/negative to Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis)
- [Adjust your alerts](#adjust-an-alert-to-prevent-false-positives-from-recurring) \(if needed\)
- [Undo remediation actions that were taken on devices](#undo-a-remediation-action-that-was-taken-on-a-device)

The following sections describe how to perform these tasks.

## Report a false positive/negative to Microsoft for analysis

Use the following table to determine where to submit false positives or false negatives for analysis.

| Item missed or wrongly detected | Service | What to do |
| --- | --- | --- |
| - Email message  <br>- Email attachment  <br>- URL in an email message  <br>- URL in an Office file | [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) | [Submit suspected spam, phish, URLs, and files to Microsoft for scanning](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin) |
| File or app on a device | [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection) | [Submit a file to Microsoft for malware analysis](https://www.microsoft.com/wdsi/filesubmission) |

## Adjust an alert to prevent false positives from recurring

Use the following table to choose the appropriate method for preventing similar false positives from recurring.

| Scenario | Service | What to do |
| --- | --- | --- |
| - An alert is triggered by legitimate use  <br>- An alert is inaccurate | [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security)  <br>or  <br>[Azure threat protection](https://learn.microsoft.com/en-us/azure/security/fundamentals/threat-detection) | [Manage alerts in Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/managing-alerts) |
| A file, IP address, URL, or domain is treated as malware on a device, even though it's safe | [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection) | [Create a custom indicator with an "Allow" action](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |

## Undo a remediation action that was taken on a device

If a remediation action was taken on an entity \(such as a device or an email message\) and the affected entity is not actually a threat, your security operations team can undo the remediation action in the [Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center).

1. Go to [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) and sign in.
2. In the navigation pane, choose **Action center**.
3. On the **History** tab, select an action that you want to undo. Its flyout pane opens.
4. In the flyout pane, select **Undo**.

Tip

See [Undo completed actions](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-actions#undo-completed-actions).

## Related content

- [View the details and results of an automated investigation](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-results)
- [Proactively hunt for threats with advanced hunting in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
