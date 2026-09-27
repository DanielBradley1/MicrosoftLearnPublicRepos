<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/asset-intelligence-client-wmi-classes -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Asset Intelligence Client WMI Classes

In Configuration Manager, the Asset Intelligence client Windows Management Instrumentation \(WMI\) classes query client computers for usage, software, and licensing data. These classes are in the root/cimv2/sms namespace.

## In This Section

| Term | Definition |
| --- | --- |
| [SMS\_AutoStartSoftware Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_autostartsoftware-client-wmi-class) | Enumerates software that starts automatically with, or immediately after, the operating system. |
| [SMS\_BrowserHelperObject Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_browserhelperobject-client-wmi-class) | Enumerates all browser helper objects on a computer. |
| [SMS\_InstalledExecutable Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_installedexecutable-client-wmi-class) | Identifies executable files associated with a software installation. |
| [SMS\_InstalledSoftware Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_installedsoftware-client-wmi-class) | Merges installed software information from multiple sources to provide categorization and Microsoft Licensing information. |
| [SMS\_InstalledSoftwareMS Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_installedsoftwarems-client-wmi-class) | Merges Microsoft-specific installed software information from multiple sources to provide categorization and Microsoft Licensing information. |
| [SMS\_Processor Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_processor-client-wmi-class) | Represents a device that can interpret a sequence of instructions on a computer that is running a Windows operating system. |
| [SMS\_SoftwareShortcut Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_softwareshortcut-client-wmi-class) | Defines a shortcut to executable files or a shortcut in a common system location. |
| [SMS\_SoftwareTag Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_softwaretag-client-wmi-class) | Indicates the presence of a software application on a computer.  <br>  <br>This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later. |
| [SMS\_SystemConsoleUsage Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_systemconsoleusage-client-wmi-class) | Defines usage data about devices, based on the system security event log. |
| [SMS\_SystemConsoleUser Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_systemconsoleuser-client-wmi-class) | Defines usage data about users, based on the system security event log. |

## Remarks

Classes related to the asset intelligence client WMI classes are:

- `SoftwareLicensingProduct` class. For more information, see [SoftwareLicensingProduct class](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/sppwmi/softwarelicensingproduct).
- `SoftwareLicensingService` class. For more information, see [SoftwareLicensingService class](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/sppwmi/softwarelicensingservice).
- `Win32_USBDevice` class. Tracks devices connected to USB ports.

## See also

[Initiate Asset Intelligence synchronization](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/asset-intelligence/how-to-initiate-a-synchronization)
