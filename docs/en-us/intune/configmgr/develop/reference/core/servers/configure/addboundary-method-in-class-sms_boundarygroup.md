<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addboundary-method-in-class-sms_boundarygroup -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddBoundary Method in Class SMS\_BoundaryGroup

The `AddBoundary` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds boundaries to this boundary group.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddBoundary(
   UInt32 BoundaryID[]
);
```

#### Parameters

`BoundaryID` Data type: `UInt32` Array

Qualifiers: \[in\]

Unique identifier of the boundary.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BoundaryGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroup-server-wmi-class)
