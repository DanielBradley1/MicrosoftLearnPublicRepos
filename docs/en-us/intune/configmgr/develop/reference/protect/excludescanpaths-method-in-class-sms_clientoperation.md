<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/excludescanpaths-method-in-class-sms_clientoperation -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ExcludeScanPaths Method in Class SMS\_ClientOperation

The `ExcludeScanPaths` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that excludes scan paths from all members in specified collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 ExcludeScanPaths
{
    [IN]    UInt64 ThreatID
    [IN]    String ExclusionSettingsUniqueID
    [IN]    String ExcludedPaths[]
    [IN]    String TargetCollectionID
    [OUT]   UInt32 OperationID
};
```

## Parameters

`ThreatID` Data type: `UInt64`

Qualifiers: \[id\("0"\), in\]

ThreatID.

`ExclusionSettingsUniqueID` Data type: `String`

Qualifiers: \[id\("1"\), in\]

ExclusionSettingsUniqueID.

`ExcludedPaths` Data type: `String Array`

Qualifiers: \[id\("2"\), in\]

ExcludedPaths.

`TargetCollectionID` Data type: `String`

Qualifiers: \[id\("3"\), in\]

TargetCollectionID.

`OperationID` Data type: `UInt32`

Qualifiers: \[id\("4"\), out\]

OperationID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
