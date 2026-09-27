<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/getclasseswithdata-method-in-class-sms_resourcemap -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetClassesWithData Method in Class SMS\_ResourceMap

The `GetClassesWithData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the names of the classes that have inventory data for a resource.

## Syntax

```
SInt32 GetClassesWithData(
     UInt32 ResourceId,
     Boolean History,
     String ClassNames[]
);
```

#### Parameters

`ResourceId` Data type: `UInt32`

Qualifiers: \[in\]

ID of the resource.

`History` Data type: `Boolean`

Qualifiers: \[in\]

TRUE to include history.

`ClassNames` Data type: `String`

Qualifiers: \[out\]

Names of classes that have inventory for the specified resource.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ResourceMap Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class)
