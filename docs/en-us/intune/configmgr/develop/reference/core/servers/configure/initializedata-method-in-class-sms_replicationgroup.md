<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/initializedata-method-in-class-sms_replicationgroup -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# InitializeData Method in Class SMS\_ReplicationGroup

The `InitializeData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, reinitializes a specific replication group between two specified sites.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 InitializeData(
     UInt32 ReplicationGroupID,
     String SiteCode1,
     String SiteCode2
);
```

#### Parameters

`ReplicationGroupID` Data type: `UInt32`

Qualifiers: \[in\]

Unique identifier of the replication group.

`SiteCode1` Data type: `String`

Qualifiers: \[in\]

Site code 1.

`SiteCode2` Data type: `String`

Qualifiers: \[in\]

Site code 2.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ReplicationGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_replicationgroup-server-wmi-class)
