<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Address false positives/negatives in Microsoft Defender for Endpoint

In endpoint protection solutions, a *false positive* is a file, process, or other entity incorrectly identified as malicious. A *false negative* is a malicious entity that the solution doesn't detect. False positives and false negatives can occur with any threat protection solution, including [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint).

Use the workflows in this article to identify the detection source, classify and suppress alerts, review remediation actions, configure exclusions, submit files for analysis, and investigate suspected false negatives. Complete the portal procedures in the [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139). If you use Microsoft Defender XDR, first identify the alert source as described in [Investigate alerts in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?tabs=settings). Continue with this article if the alert source is Defender for Endpoint.

## Prerequisites

### Supported operating systems

- Windows.

## Identify the detection source

For a false positive, first identify the detection source. Use the source to choose the appropriate response.

| Detection source | Recommended response |
| --- | --- |
| Endpoint detection and response \(EDR\) | Submit the false positive to the [Microsoft Security Intelligence submission portal](https://aka.ms/wdsi). You can also add an EDR exclusion or tune the alert. |
| Microsoft Defender Antivirus | If Microsoft Defender Antivirus is in active mode, submit the false positive to the [Microsoft Security Intelligence submission portal](https://aka.ms/wdsi). As a temporary mitigation, create a [file allow indicator](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file) or an [antivirus exclusion](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview). If Microsoft Defender Antivirus is in passive mode, EDR in block mode might detect the threat. |
| Custom threat intelligence | Review custom indicators for [file hashes](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file), [IP addresses or URLs](https://learn.microsoft.com/en-us/defender-endpoint/indicator-ip-domain), and [certificates](https://learn.microsoft.com/en-us/defender-endpoint/indicator-certificates). To update them, see [Manage indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicator-manage).  <br>  <br>A `CustomEnterpriseBlock` detection can also originate from:  <br>  <br>1. [Automated investigation and remediation](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations). Submit the false positive to the [Microsoft Security Intelligence submission portal](https://aka.ms/wdsi), or configure [automation folder exclusions](https://learn.microsoft.com/en-us/defender-endpoint/automation-folder-exclusions-configure).  <br>  <br>2. Custom detection rules based on [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview). [Manage the custom detection rule](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules).  <br>  <br>3. [EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode), [live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response), or [potentially unwanted application protection](https://learn.microsoft.com/en-us/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). Submit the false positive to the [Microsoft Security Intelligence submission portal](https://aka.ms/wdsi). As a temporary mitigation, create a [file allow indicator](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file) or an [antivirus exclusion](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview). |
| Microsoft Defender SmartScreen | [Report an unsafe site](https://www.microsoft.com/wdsi/support/report-unsafe-site) or [submit a network protection detection](https://www.microsoft.com/wdsi/support/report-exploit-guard). For more information, see [Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/windows/security/operating-system-security/virus-and-threat-protection/microsoft-defender-smartscreen/). |

## False positives and how to address them

[![Screenshot of definitions for false positives and false negatives in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-endpoint/media/false-positives-overview.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/false-positives-overview.png#lightbox)

Use the following five-part workflow to address false positives and reduce future occurrences.

[![Diagram that shows the five-part workflow for addressing false positives and false negatives.](https://learn.microsoft.com/en-us/defender-endpoint/media/false-positives-step-diagram.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/false-positives-step-diagram.png#lightbox)

## Part 1: Review and classify alerts

If an [alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) incorrectly identifies an entity as malicious or suspicious, classify the alert and consider suppressing similar alerts for that entity. You can also suppress accurate alerts for events that aren't important to your organization.

Classifying alerts helps improve threat protection and can reduce false positives and false negatives over time. Suppression rules reduce queue noise so your security team can focus on higher-priority work.

### Determine whether an alert is accurate

Before you classify or suppress an alert, determine whether the alert is accurate, a false positive, or benign.

1. On the **Alerts** page in the Defender portal at [https://security.microsoft.com/alerts](https://security.microsoft.com/alerts), select an alert.
2. Review the alert details. For more information, see [Review alerts in Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/review-alerts).
3. Depending on the alert status, take the steps described in the following table:
   | Alert assessment | What to do |
   | --- | --- |
   | The alert is accurate | Assign the alert, and then [investigate it](https://learn.microsoft.com/en-us/defender-endpoint/investigate-alerts) further. |
   | The alert is a false positive | 1. [Classify the alert](#classify-an-alert) as a false positive.  <br>  <br>2. [Suppress the alert](#suppress-an-alert).  <br>  <br>3. [Create an indicator](#indicators-for-defender-for-endpoint) for Microsoft Defender for Endpoint.  <br>  <br>4. [Submit a file to Microsoft for analysis](#part-4-submit-a-file-for-analysis). |
   | The alert is accurate, but benign \(unimportant\) | [Classify the alert](#classify-an-alert) as a true positive, and then [suppress the alert](#suppress-an-alert). |

### Classify an alert

Classify alerts as false positives or true positives in the Defender portal. Classification helps improve Defender for Endpoint so that you see more accurate alerts over time.

1. On the **Alerts** page in the Defender portal at [https://security.microsoft.com/alerts](https://security.microsoft.com/alerts), select an alert.
2. For the selected alert, select **Manage alert**. A flyout pane opens.
3. Under **Classification**, select **True positive**, **Informational, expected activity**, or **False positive**.

Tip

For more information about suppressing alerts, see [Manage Defender for Endpoint alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?toc=/defender-endpoint/toc.json&bc=/defender-endpoint/breadcrumb/toc.json#manage-alerts). If your organization uses a security information and event management \(SIEM\) server, also define a suppression rule there.

### Suppress an alert

Suppress false positives and accurate alerts for unimportant events to reduce noise in your alert queue.

1. On the **Alerts** page in the Defender portal at [https://security.microsoft.com/alerts](https://security.microsoft.com/alerts), select the alert that you want to suppress.
2. In the **Details** pane, select the ellipsis \(**...**\), and then select **Create suppression rule**.
3. Configure the suppression rule, and then select **Save**.

Tip

Need help with suppression rules? See [Suppress an alert and create a new suppression rule](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?toc=/defender-endpoint/toc.json&bc=/defender-endpoint/breadcrumb/toc.json#built-in-alert-tuning-rules).

## Part 2: Review remediation actions

[Remediation actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation#remediation-actions), such as quarantining a file or stopping a process, apply to entities detected as threats. Automated investigation and Microsoft Defender Antivirus can take the following actions automatically:

- Quarantine a file.
- Remove a registry key.
- Stop a process.
- Stop a service.
- Disable a driver.
- Remove a scheduled task.

Other actions, such as starting an antivirus scan or collecting an investigation package, occur manually or through [live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response). You can't undo actions taken through live response.

After you review alerts, [review remediation actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation). You can undo most actions caused by false positives:

- [Restore a quarantined file from the Action center](#restore-a-quarantined-file-from-the-action-center).
- [Undo multiple actions at one time](#undo-multiple-actions-at-one-time).
- [Remove a file from quarantine on multiple devices](#remove-a-file-from-quarantine-across-multiple-devices).
- [Restore a file from quarantine](#restore-a-file-from-quarantine).

After you review and undo actions caused by false positives, [review or define exclusions](#part-3-review-or-define-exclusions).

### Review completed actions

Review the Action center history to see completed remediation actions:

1. On the **Action center** page in the Defender portal at [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center), select the **History** tab.
2. Select an item to view details about the completed remediation action.

### Restore a quarantined file from the Action center

Undo a quarantine action for a single file from Action center:

1. On the **Action center** page in the Defender portal at [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center), select the **History** tab, and then select the action that you want to undo.
2. In the flyout pane, select **Undo**. If the action can't be undone, the **Undo** button isn't available. For more information, see [Undo completed actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation#undo-completed-actions).

### Undo multiple actions at one time

Undo several completed actions together from Action center:

1. On the **Action center** page in the Defender portal at [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center), select the **History** tab, and then select the actions that you want to undo.
2. In the flyout pane, select **Undo**.

### Remove a file from quarantine on multiple devices

Apply an undo action to other instances of the same quarantined file:

[![Screenshot of a quarantined file action in the Defender portal Action center.](https://learn.microsoft.com/en-us/defender-endpoint/media/autoir-quarantine-file-1.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/autoir-quarantine-file-1.png#lightbox)

1. On the **Action center** page in the Defender portal at [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center), select the **History** tab, and then select a file with the **Action type** value **Quarantine file**.
2. In the flyout pane, select **Apply to X more instances of this file**, and then select **Undo**.

### Review quarantined messages

Review quarantined email messages in Exchange message trace:

1. On the **Exchange message trace** page in the Defender portal at [https://security.microsoft.com/messagetrace](https://security.microsoft.com/messagetrace), select a message.
2. Review the message details.

### Restore a file from quarantine

If an investigation determines that a quarantined file is safe, restore it on each affected device.

The following commands open the latest Microsoft Defender Antivirus platform folder and restore all files with the specified threat name. Run them in a Command Prompt window that you opened by selecting **Run as administrator**:

Tip

The first command changes the directory to the latest version of <antimalware platform version> in `%ProgramData%\Microsoft\Windows Defender\Platform\<antimalware platform version>`. If that path doesn't exist, it goes to `%ProgramFiles%\Windows Defender`.

```dos
(set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

MpCmdRun.exe -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
```

For more information, see [Configure and manage Microsoft Defender Antivirus with the MpCmdRun command-line tool](https://learn.microsoft.com/en-us/defender-endpoint/command-line-arguments-microsoft-defender-antivirus).

Important

In some scenarios, the **ThreatName** might appear as `EUS:Win32/CustomEnterpriseBlock!cl`. Defender for Endpoint restores all custom blocked files that were quarantined on this device in the last 30 days.

A file that was quarantined as a potential network threat might not be recoverable.

A quarantined file might not be accessible if the system no longer has network credentials for the file location. This issue typically results from an expired access token for a temporary sign-in to a system or shared folder.

## Part 3: Review or define exclusions

Caution

Before you define an exclusion, review [Manage exclusions for Microsoft Defender for Endpoint and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview). Every exclusion lowers your level of protection.

An exclusion is an entity, such as a file or URL, that you exempt from remediation actions. Defender for Endpoint can still detect the entity, but it doesn't stop, quarantine, remove, or otherwise change it.

To define exclusions for Defender for Endpoint, complete the following tasks:

- [Create allow indicators for Microsoft Defender for Endpoint](#indicators-for-defender-for-endpoint).
- [Define exclusions for Microsoft Defender Antivirus](#exclusions-for-microsoft-defender-antivirus).
- For attack surface reduction \(ASR\) rules, configure [global ASR rule exclusions or per-ASR rule exclusions](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#file-and-folder-exclusions-for-asr-rules).

Note

Microsoft Defender Antivirus exclusions apply only to antivirus protection, not to other Defender for Endpoint capabilities. To exempt files from more capabilities, use [custom indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview) for Defender for Endpoint and exclusions for Microsoft Defender Antivirus.

ASR rules support global rule exclusions, per-rule exclusions, Microsoft Defender Antivirus exclusions, and allow indicators defined in custom indicators.

The procedures in this section describe how to define indicators and exclusions.

### Indicators for Defender for Endpoint

[Indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview), specifically indicators of compromise \(IoCs\), let your security operations team control the detection, prevention, and exclusion of entities. For example, you can exempt specific files from scans and remediation actions or generate alerts for files, IP addresses, or URLs.

To exempt entities in Defender for Endpoint, create allow indicators. Allow indicators apply to [next-generation protection](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows) and [automated investigation and remediation](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations).

You can create allow indicators for:

- [Files](#indicators-for-files)
- [IP addresses, URLs, and domains](#indicators-for-ip-addresses-urls-or-domains)
- [Application certificates](#indicators-for-application-certificates)

[![Screenshot of the indicator types available in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-endpoint/media/false-positives-indicators.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/false-positives-indicators.png#lightbox)

#### Indicators for files

When you [create an allow indicator for a file, such as an executable](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file), you help prevent Defender for Endpoint from blocking trusted files in your organization. Supported files include portable executable \(PE\) files, such as `.exe` and `.dll` files.

Before you create indicators for files, make sure the following requirements are met:

- Microsoft Defender Antivirus has cloud-based protection enabled. For more information, see [Manage cloud-based protection](https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus).
- The antimalware client version is 4.18.1901.x or later.
- Client devices run Windows 11 or Windows 10, version 1703 or later.
- Server devices run Windows Server 2016 or later.
- Windows Server 2012 R2 devices use the [modern unified solution](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2).
- The [block or allow feature is turned on](https://learn.microsoft.com/en-us/defender-endpoint/advanced-features).
- Devices run Azure Stack HCI OS, version 23H2 or later.

#### Indicators for IP addresses, URLs, or domains

When you [create an allow indicator for an IP address, URL, or domain](https://learn.microsoft.com/en-us/defender-endpoint/indicator-ip-domain), you help prevent Defender for Endpoint from blocking trusted network destinations.

Before you create indicators for IP addresses, URLs, or domains, make sure the following requirements are met:

- Network protection in Defender for Endpoint is enabled in block mode. For more information, see [Enable network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection).
- The antimalware client version is 4.18.1906.x or later.
- Devices run Windows 10, version 1709 or later, or Windows 11.

Custom network indicators are turned on in [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender). For more information, see [Advanced features](https://learn.microsoft.com/en-us/defender-endpoint/advanced-features).

#### Indicators for application certificates

When you [create an allow indicator for an application certificate](https://learn.microsoft.com/en-us/defender-endpoint/indicator-certificates), you help prevent Defender for Endpoint from blocking trusted applications, such as internally developed applications. The supported file extensions are `.CER` and `.PEM`.

Before you create indicators for application certificates, make sure the following requirements are met:

- Microsoft Defender Antivirus has cloud-based protection enabled. For more information, see [Manage cloud-based protection](https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus).
- The antimalware client version is 4.18.1901.x or later.
- Devices run one of the following operating systems:

  - Windows 10, version 1703 or later, or Windows 11.
  - Windows Server 2012 R2 or later with the [modern unified solution](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2).
  - Azure Stack HCI OS, version 23H2 or later.

- Virus and threat protection definitions are up to date.

Tip

You can create indicators individually or import multiple indicators at once. Each organization supports up to 15,000 indicators. You might need to collect details such as file hashes before you [create indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview).

### Exclusions for Microsoft Defender Antivirus

In general, you shouldn't need Microsoft Defender Antivirus exclusions. Define exclusions sparingly and only for files, folders, processes, and process-opened files that cause false positives. Review exclusions regularly. We recommend using [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/what-is-intune) to configure antivirus exclusions. You can also use other methods, such as [Group Policy](https://learn.microsoft.com/en-us/azure/active-directory-domain-services/manage-group-policy). For more information, see [Manage Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/preferences-setup).

For supported configuration methods and detailed procedures, see [Configure and validate exclusions for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure).

## Part 4: Submit a file for analysis

You can submit files, fileless detections, and other entities to Microsoft for analysis. Microsoft security researchers analyze submissions to improve Defender for Endpoint threat protection. Sign in to the submission site to track your submissions.

### Submit hashes for analysis

Use the [Microsoft Security Intelligence submission portal](https://aka.ms/wdsi) to submit up to 100 hashes for analysis. Include the source of each indicator of compromise \(IoC\), such as a blog post or security article.

### Submit a file for analysis

If Defender for Endpoint incorrectly detects or misses a file, submit the file for analysis:

1. Review the guidelines here: [Submit files for analysis](https://learn.microsoft.com/en-us/defender-xdr/submission-guide).
2. [Submit files in Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/admin-submissions-mde), or submit them through the [Microsoft Security Intelligence submission site](https://www.microsoft.com/wdsi/filesubmission/).

### Submit a fileless detection for analysis

If Defender for Endpoint detects malware based on behavior and you don't have a file to submit, submit the `MpSupportFiles.cab` diagnostic file instead. Use the [MpCmdRun command-line tool](https://learn.microsoft.com/en-us/defender-endpoint/command-line-arguments-microsoft-defender-antivirus) on Windows 10 or Windows 11 to generate the `.cab` file.

1. Generate `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab` as described in [Collect Microsoft Defender Antivirus diagnostic data](https://learn.microsoft.com/en-us/defender-endpoint/collect-diagnostic-data).
2. Review the guidelines here: [Submit files for analysis](https://learn.microsoft.com/en-us/defender-xdr/submission-guide).
3. Submit the `.cab` file through the [Microsoft Security Intelligence submission site](https://www.microsoft.com/wdsi/filesubmission).

### What happens after a file is submitted?

Microsoft systems scan your submission immediately and provide the latest available determination before an analyst reviews the case. If an analyst already processed the file, you might receive a determination quickly.

Microsoft prioritizes unprocessed submissions as follows:

- Files that are prevalent and might affect many devices receive higher priority.
- Submissions from authenticated customers, especially enterprise customers with valid [Software Assurance IDs \(SAIDs\)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default), receive higher priority.
- Submissions marked as high priority by SAID holders receive immediate attention.

To check the status of your submission, sign in to the [Microsoft Security Intelligence submission site](https://www.microsoft.com/wdsi/filesubmission).

Tip

To learn more, see [Submit files for analysis](https://learn.microsoft.com/en-us/defender-xdr/submission-guide#how-does-microsoft-prioritize-submissions).

## Part 5: Review and adjust your threat protection settings

If you receive many false positives, review the following threat protection settings:

- [Cloud-delivered protection](#cloud-delivered-protection)
- [Remediation for potentially unwanted applications](#remediation-for-potentially-unwanted-applications)
- [Automated investigation and remediation](#automated-investigation-and-remediation)

### Cloud-delivered protection

Check the cloud-delivered protection level for Microsoft Defender Antivirus. The default policy setting is **Not configured**, but we recommend turning on cloud-delivered protection. For configuration instructions, see [Configure cloud protection in Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure).

If your organization has [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/what-is-intune), you can use it to configure cloud-delivered protection. Intune is a separate product and isn't included in all subscriptions. For licensing information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses). You can also use other methods described in the configuration article, such as [Group Policy](https://learn.microsoft.com/en-us/azure/active-directory-domain-services/manage-group-policy).

### Remediation for potentially unwanted applications

Potentially unwanted applications \(PUA\) are software that can cause devices to run slowly, display unexpected ads, or install other unexpected software. Examples include advertising, bundling, and evasion software that behaves differently when security products are present. Although PUA isn't malware, security products classify some software as PUA based on its behavior and reputation.

To learn more about PUA, see [Detect and block potentially unwanted applications](https://learn.microsoft.com/en-us/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

Your PUA protection settings might cause false positives for apps that your organization uses. If needed, run PUA protection in audit mode temporarily or apply it to a subset of devices. You can configure PUA protection for Microsoft Edge and Microsoft Defender Antivirus.

If your organization has [Microsoft Intune](https://learn.microsoft.com/en-us/intune/endpoint-manager-overview), we recommend using it to configure PUA protection. Intune is a separate product and isn't included in all subscriptions. For licensing information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses). If you don't have Intune, use another method in [Configure PUA protection in Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus#configure-pua-protection-in-microsoft-defender-antivirus), such as [Group Policy](https://learn.microsoft.com/en-us/azure/active-directory-domain-services/manage-group-policy).

### Automated investigation and remediation

[Automated investigation and remediation](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations) \(AIR\) examines alerts and can take immediate action to resolve breaches. During an automated investigation, AIR assigns each piece of evidence a verdict: *Malicious*, *Suspicious*, or *No threats found*.

Depending on your organization's [automation level](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels) and other security settings, AIR can remediate artifacts with *Malicious* or *Suspicious* verdicts automatically, manually, or after approval by your security operations team.

- [Review automation levels](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels).
- [Configure AIR capabilities in Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-automated-investigations-remediation).

Important

We recommend using *Full automation* for automated investigation and remediation. Don't turn off AIR because of a false positive. Instead, [define exceptions with allow indicators](#indicators-for-defender-for-endpoint) and keep AIR configured to take appropriate actions automatically. Following the [automation-level guidance](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels#levels-of-automation) helps reduce the number of alerts your security operations team handles.

## False negatives and how to address them

A false negative occurs when a malicious entity \(such as a file, process, or network connection\) isn't detected by Defender for Endpoint. False negatives can result from outdated security intelligence, misconfigured features, or threats that evade existing signatures.

Note

Some capabilities in this section depend on your plan. Advanced hunting, collecting an investigation package, and [EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode) require [Microsoft Defender for Endpoint Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint). The device timeline requires Defender for Endpoint Plan 2 or [Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview). These capabilities aren't available in Defender for Endpoint Plan 1.

### Verify a suspected false negative

Before you report a false negative, confirm that the suspicious activity occurred without a corresponding detection. Compare endpoint behavior in the device timeline with advanced hunting results in the Defender portal.

1. On the **Device inventory** page of the Defender portal at [https://security.microsoft.com/machines](https://security.microsoft.com/machines), select the affected device.
2. On the device entity page that opens, select the **Timeline** tab and look for events that correspond to the suspicious activity \(for example, file creation, process execution, or network connections during the expected time frame\).
3. On the **Advanced hunting** page in the Defender portal at [https://security.microsoft.com/v2/advanced-hunting](https://security.microsoft.com/v2/advanced-hunting), query the relevant tables for activity throughout your environment. For example, the following query finds file-creation events for a specific file hash:

   ```kusto
   DeviceFileEvents
   | where SHA1 == "<hash>"
   | where ActionType == "FileCreated"
   ```


   The following query finds network activity for a suspicious domain:


   ```kusto
   DeviceNetworkEvents
   | where RemoteUrl has "<suspicious-domain>"
   ```

4. If the logs contain the activity but Defender for Endpoint didn't generate an alert, collect evidence for escalation.

### Collect evidence for false negative escalation

Before you submit a false negative to Microsoft, gather the following forensic artifacts:

- **Endpoint support files**: Generate the diagnostic package `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab` by running `MpCmdRun.exe -GetFiles` in an elevated Command Prompt. For instructions, see [Collect Microsoft Defender Antivirus diagnostic data](https://learn.microsoft.com/en-us/defender-endpoint/collect-diagnostic-data).
- **Process execution details**: Document the process tree, command-line parameters, and parent processes associated with the suspicious activity. Find these details in the device timeline or query the [`DeviceProcessEvents`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceprocessevents-table) table in advanced hunting.
- **Network flow data**: If the threat involves network connections, capture relevant connection details \(remote IPs, domains, ports\) from the [`DeviceNetworkEvents`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicenetworkevents-table) table.
- **Memory dumps or sandbox traces**: If possible, capture memory dumps or sandbox execution traces from the affected device to help Microsoft analyze the threat behavior. You can also [collect an investigation package from the device](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts#collect-investigation-package-from-devices) in the Defender portal.
- **Raw event data**: [Export relevant events](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-results#export-tables-and-charts) from advanced hunting in the Microsoft Defender portal for inclusion in your submission.

### Submit false negatives for analysis

After you gather the evidence, submit the false negative to Microsoft by using one of the following methods:

- On the **Submissions** page in the Defender portal at [https://security.microsoft.com/reportsubmission](https://security.microsoft.com/reportsubmission):

  - **Files** tab: For complete instructions, see [Submit files in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/admin-submissions-mde).
  - **URLs** tab: For complete instructions, see [Report questionable URLs to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-questionable-urls-to-microsoft).

- Submit hashes and files directly at the [Microsoft Security Intelligence submission site](https://www.microsoft.com/wdsi/filesubmission/). For more information, see [Submit files for analysis](https://learn.microsoft.com/en-us/defender-xdr/submission-guide).

### Mitigate threats while awaiting analysis

After you submit a false negative, the threat might remain active in your environment. Use [custom indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file) in Defender for Endpoint to block known malicious entities until Microsoft updates its detections:

- **File hashes**: Create block indicators for malicious file hashes. See [Create indicators for files](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file).
- **IP addresses and domains**: Create block indicators for malicious IPs or domains. See [Create indicators for IPs and URLs/domains](https://learn.microsoft.com/en-us/defender-endpoint/indicator-ip-domain).

Custom indicators apply throughout your organization and provide immediate protection while Microsoft analyzes the submission.

### Check endpoint health and configuration

Outdated security intelligence or disabled protection features can cause false negatives. Check endpoint health on the affected device:

1. Run the following command in an elevated PowerShell window to check the engine and security intelligence versions:

   ```powershell
   Get-MpComputerStatus | Select-Object AMServiceVersion, AMProductVersion, AMEngineVersion, AntispywareSignatureVersion, AntivirusSignatureVersion
   ```

2. Confirm that security intelligence updates are current. If the versions are outdated, run the following command to update them:

   ```powershell
   Update-MpSignature
   ```


   Note


   You can also check for security intelligence updates from an elevated Command Prompt by running `MpCmdRun.exe -SignatureUpdate`. For more information, see [Use the command line to manage Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/command-line-arguments-microsoft-defender-antivirus).

3. Verify that key protection features are enabled. False negatives can occur if the following features are disabled or misconfigured:

   - [Cloud-delivered protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure)
   - [Real-time protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus)
   - [EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode)
   - [Attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-overview)

4. Check that the device platform and operating system are up to date. Older builds might not include detection capabilities available in newer versions.

## Still need help?

If the issue remains after you complete the workflows in this article, contact Microsoft support.

1. In the upper-right corner of the Defender portal at [https://security.microsoft.com](https://security.microsoft.com), select the question mark \(**?**\), and then select **Microsoft support**.
2. In the **Support Assistant** window, describe your issue, and then send your message. From there, you can open a service request.

## See also

- [Manage Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/preferences-setup)
- [Manage exclusions for Microsoft Defender for Endpoint and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview)
- [Microsoft Defender portal overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
- [Configure Microsoft Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
