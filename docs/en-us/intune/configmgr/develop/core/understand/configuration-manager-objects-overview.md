<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Objects Overview

The Configuration Manager objects are instances of Configuration Manager-specific Windows Management Instrumentation \(WMI\) classes that are managed by the SMS Provider. The Configuration Manager object class categories are described in the following table.

| Configuration Manager Object Class Category | Description |
| --- | --- |
| Software distribution | Objects associated with the software distribution feature of Configuration Manager, such as advertisement, collection, package, and program objects. |
| Scheduling | Organizes scheduled Configuration Manager events, such as inventory updates. |
| Site | Contains information about Configuration Manager sites. |
| Security | Describes the permissions granted to users and user groups to operate on specific Configuration Manager-secured objects, such as program and package objects. |
| Query | Describes Configuration Manager site database queries. |
| Resource | Populated when Configuration Manager discovers potential client computers, users, user groups, and other types of objects within the boundaries of the site. |
| Inventory | Provides the structure for inventory operations on Configuration Manager client systems, users, and user groups. |
| Software metering | Describes the metered Configuration Manager resources, such as program files. |
| Status and summarizer | Indicates the status of Configuration Manager sites, components, and software distribution operations. |
| Collected files | Contains information about files collected from clients. |

## DebugView

To show SMS Provider object property values in the Configuration Manager console results pane, start the console with the following command line:

<InstallationDirectory>\\Microsoft.ConfigurationManagement.exe /SMS:DebugView=1

For more information, see [Configuration Manager console command-line options](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console#command-line-options).

## See Also

[Configuration Manager Association Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/association-classes) [Configuration Manager Bit Field Properties](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-bit-field-properties) [Configuration Manager console command-line options](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console#command-line-options) [Configuration Manager Date and Time Formats](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/date-and-time-formats) [Configuration Manager Embedded Objects](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/embedded-objects) [Configuration Manager Extended WMI Query Language](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [Configuration Manager Lazy Properties](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-lazy-properties) [About errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors) [Configuration Manager Object Security](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-object-security) [Configuration Manager Special Queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries)
