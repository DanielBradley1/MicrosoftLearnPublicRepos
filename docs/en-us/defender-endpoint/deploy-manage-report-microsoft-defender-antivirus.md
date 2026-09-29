<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Deploy, manage, and report on Microsoft Defender Antivirus

You can manage and report on Microsoft Defender Antivirus using one of several tools, such as:

- [Deploy, manage, and report on Microsoft Defender Antivirus](#deploy-manage-and-report-on-microsoft-defender-antivirus)

  - [Microsoft Intune](#microsoft-intune)
  - [Configuration Manager](#configuration-manager)
  - [PowerShell](#powershell)
  - [Group Policy and Microsoft Entra ID](#group-policy-and-microsoft-entra-id)
  - [Windows Management Instrumentation](#windows-management-instrumentation)

This article describes these options for deployment, management, and reporting.

## Prerequisites

### Supported operating systems

Microsoft Defender Antivirus is installed as a core part of Windows 10 and 11, and is included in Windows Server 2016 and later.

Note

Windows Server 2012 requires Microsoft Defender for Endpoint.

## Microsoft Intune

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

With Intune, you can manage device security through policies, such as a policy to configure Microsoft Defender Antivirus and other security capabilities in Defender for Endpoint. To learn more, see [Use policies to manage device security](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security#use-policies-to-manage-device-security).

For reporting, you can choose from several options:

- [Use the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal), which includes a [device inventory list](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview). To access the device inventory, in the Microsoft Defender portal \([https://security.microsoft.com/](https://security.microsoft.com/)\), go to **Assets** > **Devices**. The device inventory list displays onboarded devices along with their health state and risk level.
- [Manage devices with Intune](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-management), which includes the ability to view detailed information about devices and take action. [Available actions](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-management#available-device-actions) include starting an antivirus scan, restarting a device, locating a device, wiping a device, and more.

## Configuration Manager

With Configuration Manager, you can manage security and malware on Configuration Manager client computers. Use the [Endpoint Protection point site system role](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-site-role) and [enable Endpoint Protection with custom client settings](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-configure-client). You can use [default and customized antimalware policies](https://learn.microsoft.com/en-us/defender-office-365/anti-malware-policies-configure).

For reporting, you can choose from several options:

- [Use the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal), which includes a [device inventory list](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview). To access the device inventory, in the Microsoft Defender portal \([https://security.microsoft.com/](https://security.microsoft.com/)\), go to **Assets** > **Devices**. The device inventory list displays onboarded devices along with their health state and risk level.
- [Use Intune to view device details](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-inventory).
- Use the default [Configuration Manager Monitoring workspace](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/monitor-applications-from-the-console).
- [Create email alerts](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-configure-alerts).
- If your organization has Defender for Endpoint, you can also use the [Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal), which includes a [device inventory list](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview). To access the device inventory, in the Microsoft Defender portal \([https://security.microsoft.com/](https://security.microsoft.com/)\), go to **Assets** > **Devices**. The device inventory list displays onboarded devices along with their health state and risk level.

## PowerShell

You can use PowerShell with Group Policy or Configuration Manager to manage Microsoft Defender Antivirus on client devices. You can also use PowerShell to manage Microsoft Defender Antivirus manually on individual devices that aren't managed by a security team.

- Use the appropriate [Get- cmdlets available in the Defender module](https://learn.microsoft.com/en-us/powershell/module/defender).
- Use the [Set-MpPreference](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference) and [Update-MpSignature](https://learn.microsoft.com/en-us/powershell/module/defender/update-mpsignature) cmdlets that are available in the Defender module.

For reporting, you can choose from the following options:

- [Use the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal), which includes a [device inventory list](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview). To access the device inventory, in the Microsoft Defender portal \([https://security.microsoft.com/](https://security.microsoft.com/)\), go to **Assets** > **Devices**. The device inventory list displays onboarded devices along with their health state and risk level.
- [Use Intune to view device details](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-inventory).
- Use the default [Configuration Manager Monitoring workspace](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/monitor-applications-from-the-console).

## Group Policy and Microsoft Entra ID

You can use a Group Policy Object to deploy configuration changes and ensure Microsoft Defender Antivirus is enabled. Use Group Policy Objects \(GPOs\) to [configure update options for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-update-schedule-microsoft-defender-antivirus) and [configure Windows Defender features](https://learn.microsoft.com/en-us/defender-endpoint/configure-microsoft-defender-antivirus-features).

For reporting, keep in mind that device reporting isn't available with Group Policy.

- You can generate a list of Group Policies to determine if any settings or policies aren't applied.
- If your organization has Defender for Endpoint, you can also use the [Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal), which includes a [device inventory list](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview). To access the device inventory, in the Microsoft Defender portal \([https://security.microsoft.com/](https://security.microsoft.com/)\), go to **Assets** > **Devices**. The device inventory list displays onboarded devices along with their health state and risk level.

## Windows Management Instrumentation

With Windows Management Instrumentation \(WMI\), you can manage Microsoft Defender Antivirus with Group Policy or Configuration Manager. You can also use WMI to manage Microsoft Defender Antivirus manually on individual devices that aren't managed by a security team.

- Use the [Set method of the MSFT\_MpPreference class](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/set-msft-mppreference) and the [Update method of the MSFT\_MpSignature class](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/update-msft-mpsignature).
- Use the [MSFT\_MpComputerStatus](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/msft-mpcomputerstatus) class and the get method of associated classes in the [Windows Defender WMIv2 Provider](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-providers).

For reporting, Windows events comprise several security event sources, including Security Account Manager \(SAM\) events \([enhanced for Windows 10](https://learn.microsoft.com/en-us/windows/whats-new/whats-new-windows-10-version-1507-and-1511)\). Also see [Security auditing](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/security-auditing-overview) and [Windows Defender events](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-microsoft-defender-antivirus).

## See also

- [Microsoft Defender Antivirus compatibility with other security products](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility)
- [Deploy and enable Microsoft Defender Antivirus protection](https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus)
- [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates)
- [Monitor and report on Microsoft Defender Antivirus protection](https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

Tip

**Performance tip**: Due to various factors, Microsoft Defender Antivirus, like other antivirus software, can cause performance issues on endpoint devices. In some cases, you might need to tune the performance of Microsoft Defender Antivirus to alleviate those performance issues. Microsoft's **Performance analyzer** is a PowerShell command-line tool that helps determine which files, file paths, processes, and file extensions might be causing performance issues. You can use the information gathered using Performance analyzer to better assess performance issues and apply remediation actions. See [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus).
