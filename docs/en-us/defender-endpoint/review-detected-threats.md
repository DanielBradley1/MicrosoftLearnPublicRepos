<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/review-detected-threats -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Microsoft Defender for Endpoint Antivirus and Intune integration

This article explains how to use the Microsoft Defender for Endpoint Antivirus and Microsoft Intune integration to review and manage threat detections on enrolled devices. You can view active malware reports in the Microsoft Defender portal and take remediation actions through the Microsoft Intune admin center.

## Prerequisites

### Supported operating systems

The Microsoft Defender for Endpoint Antivirus and Intune integration supports threat detection and management on the following operating systems:

- Windows
- macOS
- Android

In the Microsoft Defender portal, you can view and manage threat detections using the following steps:

1. Visit the [Microsoft Defender portal](https://security.microsoft.com) and sign-in.

   On the landing page, you see the **Devices with active malware** card with the following information:

   - Display text: Applies to Intune-managed devices. Devices with multiple malware detections may be counted more than once.
   - Last updated date and time.
   - A bar with the Active and Malware remediated portions as per your scan.


   You can select **View Details** for more information.

2. After the malware detection is remediated, you see the following text:

   *Malware found on your devices have been remediated successfully*.

## Manage threat detections in Microsoft Intune

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To manage threat detections for any devices that are [enrolled in Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/deployment-guide-enrollment), see [Security reports](https://learn.microsoft.com/en-us/intune/device-management/reports/overview#security-reports) \(opens in a new tab in the Intune documentation\).

## FAQs

The following questions address common issues with malware detection reporting and the Intune integration.

### In the Microsoft Defender portal > Devices with active malware > Devices with malware detections report, why does the Last update seem to be occurring today?

To see when the malware was detected, you can take the following steps:

1. Since the malware detection data is managed through the Intune integration, visit the [**Intune portal**](https://intune.microsoft.com) and select **Antivirus**, and then select the **Active malware** tab.
2. Select **Export**.
3. On your device, go to Downloads, and extract the `Active malware_YYYY_MM_DD_THH_MM_SS.0123Z.csv.zip` file.
4. Open the CSV and find the **LastStateChangeDateTime** column to see when malware was detected.

### In the devices with malware detections report, why can't I see any information about which malware was detected on the device?

To see the malware name, visit the [Intune portal](https://intune.microsoft.com). Because Microsoft Defender for Endpoint Antivirus is integrated with Intune, select **Antivirus**, and then select the **Active malware** tab to view the **Malware name** column.

### I see a different number for active malware in Devices with active malware report, when compared to numbers I see using Reports > Detected malware, and Intune > Antivirus > Active malware

The **Devices with active malware** report is based on the devices that were active within the last 1 day \(24 hours\) and had malware detections within the last 15 days.

[Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) is a query-based threat-hunting tool in the Microsoft Defender portal that lets you inspect device and alert data. Use the following Advanced Hunting query to identify onboarded, active devices that had antivirus-detected malware in the last 15 days, along with the associated alert details:

```kusto
DeviceInfo
| where Timestamp > startofday(datetime(2024-01-29 00:00:00))
| where OnboardingStatus == "Onboarded"
| where SensorHealthState == "Active"
| distinct DeviceId, DeviceName
| join kind=innerunique (
AlertEvidence
| where Timestamp > ago(15d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| where DetectionSource == "Antivirus")
on DeviceName
| distinct DeviceName, DeviceId, Title, AlertId, Timestamp
```

### I searched the computer name in the top search bar and got two devices with the same name. I don't know which one of those two devices the report is referring to?

To identify the correct device, use the following [Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) query \(a query-based threat-hunting tool in the Microsoft Defender portal\) to retrieve details such as the unique DeviceID, Title, AlertID, and timestamp. The query joins onboarded active devices with antivirus alert evidence from the last 15 days, returning distinct entries per device:

```kusto
DeviceInfo
| where Timestamp > startofday(datetime(2024-01-29 00:00:00))
| where OnboardingStatus == "Onboarded"
| where SensorHealthState == "Active"
| distinct DeviceId, DeviceName
| join kind=innerunique (
AlertEvidence
| where Timestamp > ago(15d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| where DetectionSource == "Antivirus")
on DeviceName
| distinct DeviceName, DeviceId, Title, AlertId, Timestamp
```

The unique `DeviceId` value distinguishes the two devices with the same name. After identifying, work with your IT admin's to make sure that the devices are uniquely named. If a device is retired, use [device tags to mark it as decommissioned](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/how-to-use-tagging-effectively-part-1/ba-p/1964058).

### I see malware detection in Intune and on the Devices with active malware report, but I don't see it in the MDE Alerts queue or in the Incidents queue

[Cloud Protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-network-connections-microsoft-defender-antivirus) isn't allowed through your firewall or proxy.

Do the following procedure to verify that your network can communicate with the Microsoft Defender Antivirus cloud service:

In an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\), run the following commands to switch to the current Microsoft Defender platform directory and validate MAPS \(cloud protection\) connectivity:

Tip

The first command changes the directory to the latest version of <antimalware platform version> in `%ProgramData%\Microsoft\Windows Defender\Platform\<antimalware platform version>`. If that path doesn't exist, it goes to `%ProgramFiles%\Windows Defender`.

```dos
(set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

MpCmdRun.exe -ValidateMapsConnection
```

For more information about MpCmdRun, see [Configure and manage Microsoft Defender Antivirus with the MpCmdRun command-line tool](https://learn.microsoft.com/en-us/defender-endpoint/command-line-arguments-microsoft-defender-antivirus).

### I see a device that has been inactive for 180+ days but still showing up on the report for 'Devices with active malware'. The device doesn't show in the "Device inventory", can't be turned on and can't be offboarded from Microsoft Defender for Endpoint

The device has not been [retired or wiped using Intune remote actions](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/devices-wipe).

## Related content

- [Alerts in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/investigate-alerts)
- [Alerts queue in Microsoft Defender](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue-endpoint-detection-response)
