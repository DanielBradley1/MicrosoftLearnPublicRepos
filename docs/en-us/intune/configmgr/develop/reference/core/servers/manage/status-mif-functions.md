<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/status-mif-functions -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Status MIF Functions

In Configuration Manager, status MIF functions are provided in separate libraries to create a status Management Information Format \(MIF\) file. For more information about how the install status MIF file is used by Configuration Manager, see [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class).

Success or failure of an advertisement is determined by using either an install status MIF file or the exit code of the advertised program. Relying on the exit code limits the visibility of events during the installation process and requires interpretation of the various exit codes. However, using the install status MIF file provides an enhanced status indicating whether the installation succeeded or failed, and it includes an appropriate description.

## Status MIF Functions

- [Create Function](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/create-function)
- [InstallStatusMIF Function](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/installstatusmif-function)
- [InstallStatusMIFEx Function](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/installstatusmifex-function)
