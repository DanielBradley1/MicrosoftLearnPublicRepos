<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/hardware-inventory-server-wmi-classes -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Hardware inventory server WMI classes

The Configuration Manager hardware inventory server WMI classes are generated dynamically.

During the Configuration Manager hardware inventory process, the name for a class is transformed from "Win32\_hardware" to "SMS\_G\_System\_hardware". For example, "Win32\_DiskDrive" translates to "SMS\_G\_System\_DISK".

In addition to the class name change, the following differences are found between the Win32 classes and the Configuration Manager hardware inventory server classes:

- Each Configuration Manager class inherits four properties from [SMS\_G\_System\_Current Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class).
- The Configuration Manager hardware inventory classes don't support the Win32 class methods.
- Many of the Configuration Manager hardware inventory classes contain a subset of the Win32 class properties.
