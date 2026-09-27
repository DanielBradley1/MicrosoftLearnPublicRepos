<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/excludeandinclude-method-in-class-sms_migrationentity -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# ExcludeAndInclude Method in Class SMS\_MigrationEntity

The `ExcludeAndInclude` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, marks the entities as excluded or included.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ExcludeAndInclude(  
     UInt32 excludeEntityList[],  
     UInt32 includeEntityList[]  
);  
```

#### Parameters

`excludeEntityList`  
Data type: `UInt32` Array

Qualifiers: \[in\]

List of entities excluded.

`includeEntityList`  
Data type: `UInt32` Array

Qualifiers: \[in\]

List of entities included.

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
