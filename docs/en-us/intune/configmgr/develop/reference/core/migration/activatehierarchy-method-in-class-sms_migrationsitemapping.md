<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/activatehierarchy-method-in-class-sms_migrationsitemapping -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# ActivateHierarchy Method in Class SMS\_MigrationSiteMapping

The `ActivateHierarchy` WMI class method in Configuration Manager activates the hierarchy.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ActivateHierarchy (  
     String sourceSite,  
     String wmiAccount,  
     String sqlAccount,  
     String destinationSiteCode,  
     String scheduleToken  
);  
```

#### Parameters

`sourceSite`  
Data type: `String` Array

Qualifiers: \[in\]

The source site FQDN, netBIOS name or IP address.

`wmiAccount`  
Data type: `String` Array

Qualifiers: `[in]`

The account name to access the WMI provider on the source site.

`sqlAccount`  
Data type: `String` Array

Qualifiers: \[in\]

The account name to access SQL Server on the source site.

`destinationSiteCode`  
Data type: `String` Array

Qualifiers: `[in]`

The destination site's site code. This should be the top site.

`scheduleToken`  
Data type: `String` Array

Qualifiers: \[in\]

The schedule for the data gathering job.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_MigrationEntity Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationentity-server-wmi-class)
