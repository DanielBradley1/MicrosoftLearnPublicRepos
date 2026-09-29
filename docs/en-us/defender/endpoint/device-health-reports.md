<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/device-health-reports -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Device health reports in Microsoft Defender for Endpoint

- [Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview)

The Device Health report provides information about the devices in your organization. The Device Health report includes trending information showing the sensor health state, antivirus status, OS platforms, Windows 10 versions, and Microsoft Defender Antivirus update versions.

Important

For Windows Server 2012 R2 and Windows Server 2016 to appear in device health reports, these devices must be onboarded using the modern unified solution package. For more information, see [New functionality in the modern unified solution for Windows Server 2012 R2 and 2016](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2).

In the Microsoft Defender portal navigation panel, select **Reports**, and then open **Device health and compliance**. The **Device health and compliance** dashboard in the Microsoft Defender portal is structured in two tabs:

- The [**Sensor health & OS** tab](https://learn.microsoft.com/en-us/defender-endpoint/device-health-sensor-health-os#sensor-health--os-tab) provides general operating system information, divided into three cards that display the following device attributes:

  - [Sensor health card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-sensor-health-os#sensor-health-card)
  - [Operating systems and platforms card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-sensor-health-os#operating-systems-and-platforms-card)
  - [Windows versions card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-sensor-health-os#windows-versions-card)

- The [**Microsoft Defender Antivirus health** tab](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#microsoft-defender-antivirus-health-tab) has eight cards that report on aspects of Microsoft Defender Antivirus:

  - [Antivirus mode card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#antivirus-mode-card)
  - [Antivirus engine version card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#antivirus-engine-version-card)
  - [Antivirus security intelligence version card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#antivirus-security-intelligence-version-card)
  - [Antivirus platform version card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#antivirus-platform-version-card)
  - [Recent antivirus scan results card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#recent-antivirus-scan-results-card)
  - [Antivirus engine updates card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#antivirus-engine-updates-card)
  - [Security intelligence updates card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#security-intelligence-updates-card)
  - [Antivirus platform updates card](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health#antivirus-platform-updates-card)

## Report access permissions

To access the Device Health report \(the **Device health and compliance** dashboard\) in the Microsoft Defender portal, the following permissions are required:

| Permission name | Permission type |
| :--- | :--- |
| View Data | Threat and vulnerability management \(TVM\) |

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To assign the View Data - Threat and vulnerability management \(TVM\) permission for the Device health and antivirus compliance report:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com) using account with Security administrator or Global administrator role assigned.
2. In the navigation pane, select **Settings** > **Endpoints** > **Roles** \(under **Permissions**\).
3. Select the role you'd like to edit.
4. Select **Edit**.
5. In **Edit role**, on the **General** tab, in **Role name**, type a name for the role.
6. In **Description** type a brief summary of the role.
7. In **Permissions**, select **View Data**, and under **View Data** select **Threat and vulnerability management** \(TVM\).

## Related content

Tip

**Performance tip** Due to a variety of factors \(examples listed below\) Microsoft Defender Antivirus, like other antivirus software, can cause performance issues on endpoint devices. In some cases, you might need to tune the performance of Microsoft Defender Antivirus to alleviate those performance issues. Microsoft's **Performance analyzer** is a PowerShell command-line tool that helps determine which files, file paths, processes, and file extensions might be causing performance issues; some examples are:

- Top paths that impact scan time
- Top files that impact scan time
- Top processes that impact scan time
- Top file extensions that impact scan time
- Combinations – for example:

  - top files per extension
  - top paths per extension
  - top processes per path
  - top scans per file
  - top scans per file per process

You can use the information gathered using Performance analyzer to better assess performance issues and apply remediation actions. See: [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus).

### See also

- [Create and manage roles for role-based access control](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- [Export device antivirus health details API methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/device-health-api-methods-properties)
