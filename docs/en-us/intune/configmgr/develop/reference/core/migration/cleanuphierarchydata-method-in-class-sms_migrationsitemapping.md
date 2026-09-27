<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/cleanuphierarchydata-method-in-class-sms_migrationsitemapping -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# CleanupHierarchyData Method in Class SMS\_MigrationSiteMapping

The `CleanupHierarchyData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, cleans up hierarchy data.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CleanupHierarchyData(  
     UInt32 siteID   
);  
```

#### Parameters

`siteID`  
Data type: `UInt32` Array

Qualifiers: \[in\]

Site ID of the Configuration Manager site.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_MigrationSiteMapping Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationsitemapping-server-wmi-class)
