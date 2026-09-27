<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/allowthreat-method-in-class-sms_clientoperation -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AllowThreat Method in Class SMS\_ClientOperation

The `AllowThreat` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that allows the specified threat \(identified by `ThreatID`\) to all members in a specific collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 AllowThreat
{
    [IN]    UInt64 ThreatID
    [IN]    String AllowSettingsUniqueID
    [IN]    String TargetCollectionID
    [OUT]   UInt32 OperationID
};
```

## Parameters

`ThreatID` Data type: `UInt64`

Qualifiers: \[id\("0"\), in\]

Threat identifier.

`AllowSettingsUniqueID` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Antimalware settings \(with allow threat identifier enabled\) unique identifier.

`TargetCollectionID` Data type: `String`

Qualifiers: \[id\("2"\), in\]

Identifier of target collection.

`OperationID` Data type: `UInt32`

Qualifiers: \[id\("3"\), out\]

Unique identifier for the operation.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ClientOperation Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_clientoperation-server-wmi-class)
