<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Overview of automated investigations

Automated investigation and response \(AIR\) in Microsoft Defender for Endpoint automatically examines alerts and takes immediate action to resolve breaches. This article provides an overview of AIR capabilities, prerequisites, and how the process works.

## Prerequisites

To use automated investigation and response \(AIR\), your subscription must include [Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) or [Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview).

Important

As of September 1, 2026, Automated Investigation and Response \(AIR\) will no longer run as a separate investigation experience or be available for manual triggering in Microsoft Defender.

AIR detection and response capabilities are already included in Microsoft Defender's default antivirus protection stack and run automatically. For on-demand investigations, run a full antivirus scan as needed.

Note

- Automated investigation and response \(AIR\) requires Microsoft Defender Antivirus for running in passive mode or active mode. If Microsoft Defender Antivirus is disabled or uninstalled, Automated Investigation and Response will not function correctly.
- Automated investigation and response on Windows Server 2012 R2 and Windows Server 2016 requires the [Unified Agent](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2) to be installed.

### Supported operating systems

Automated investigation and response is supported on the following operating systems:

- Windows Server 2012 R2 \(Preview\)
- Windows Server 2016 \(Preview\)
- Windows Server 2019 and later
- Windows 10, version 1709 \(OS Build 16299.1085 with [KB4493441](https://support.microsoft.com/servicing/os/windows-10/2019/04/april-9-2019-kb4493441-os-build-16299-1087)\) or later
- Windows 10, version 1803 \(OS Build 17134.704 with [KB4493464](https://support.microsoft.com/servicing/os/windows-10/2019/04/april-9-2019-kb4493464-os-build-17134-706)\) or later
- Windows 10, version [1803 release information](https://learn.microsoft.com/en-us/windows/release-information/status-windows-10-1809-and-windows-server-2019) or later
- Windows 11
- Azure Stack HCI OS, version 23H2 and later

Want to see how automated investigation and response works? Watch the following video:

<iframe src="https://learn-video.azurefd.net/vod/player?id=f7299926-ec86-40f6-9188-372304ab80f9" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

The technology in automated investigation uses various inspection algorithms and is based on processes that are used by security analysts. AIR capabilities are designed to examine alerts and take immediate action to resolve breaches. AIR capabilities significantly reduce alert volume, allowing security operations to focus on more sophisticated threats and other high-value initiatives. All remediation actions, whether pending or completed, are tracked in the [Action center](https://learn.microsoft.com/en-us/defender-endpoint/auto-investigation-action-center). In the Action center, pending actions are approved \(or rejected\), and completed actions can be undone if needed.

This article provides an overview of automated investigation and response \(AIR\) and includes links to next steps and additional resources.

## How the automated investigation starts

An automated investigation can start when an alert is triggered or when a security operator initiates the investigation.

| Situation | What happens |
| --- | --- |
| An alert is triggered | In general, an automated investigation starts when an [alert is triggered](https://learn.microsoft.com/en-us/defender-endpoint/review-alerts), and an [incident is created](https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue). For example, suppose a malicious file resides on a device. When that file is detected, an alert is triggered, and incident is created. An automated investigation process begins on the device. As other alerts are generated because of the same file on other devices, they are added to the associated incident and to the automated investigation. |
| An investigation is started manually | An automated investigation can be started manually by your security operations team. For example, suppose a security operator is reviewing a list of devices and notices that a device has a high risk level. The security operator can select the device in the list to open its flyout, and then select **Initiate Automated Investigation**. |

## How an automated investigation expands its scope

While an investigation is running, any other alerts generated from the device are added to an ongoing automated investigation until that investigation is completed. In addition, if the same threat is seen on other devices, those devices are added to the investigation.

If an incriminated entity is seen in another device, the automated investigation process expands its scope to include that device, and a general security playbook starts on that device. If 10 or more devices are found during this expansion process from the same entity, then that expansion action requires an approval, and is visible on the **Pending actions** tab.

## How threats are remediated

As alerts are triggered, and an automated investigation runs, a verdict is generated for each piece of evidence investigated. Verdicts can be:

- *Malicious*;
- *Suspicious*; or
- *No threats found*.

As verdicts are reached, automated investigations can result in one or more remediation actions. Examples of remediation actions include sending a file to quarantine, stopping a service, removing a scheduled task, and more. For a complete list, see [Remediation actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation#remediation-actions).

Depending on the [level of automation](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels) set for your organization, as well as other security settings, remediation actions can occur automatically or only upon approval by your security operations team. Additional security settings that can affect automatic remediation include [protection from potentially unwanted applications](https://learn.microsoft.com/en-us/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) \(PUA\).

All remediation actions, whether pending or completed, are tracked in the [Action center](https://learn.microsoft.com/en-us/defender-endpoint/auto-investigation-action-center). If necessary, your security operations team can undo a remediation action. To learn more, see [Review and approve remediation actions following an automated investigation](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation).

Tip

Check out the new, unified investigation page in the Microsoft Defender portal. To learn more, see [Unified investigation page](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-results#new-unified-investigation-page).

## Next steps

Use the following resources to continue configuring and learning about automated investigation and response:

- [Automation levels](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels)
- [See the interactive guide: Investigate and remediate threats with Microsoft Defender for Endpoint](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Configure automated investigation and remediation capabilities in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-automated-investigations-remediation)

## See also

For related information, see the following articles:

- [PUA protection](https://learn.microsoft.com/en-us/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Automated investigation and response in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/air-about)
- [Automated investigation and response in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir)
