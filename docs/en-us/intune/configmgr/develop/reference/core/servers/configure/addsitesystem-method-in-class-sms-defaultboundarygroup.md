<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addsitesystem-method-in-class-sms-defaultboundarygroup -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddSiteSystem Method in Class SMS\_DefaultBoundaryGroup

The `AddSiteSystem` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds one or more site system servers to a default boundary group.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddSiteSystem(
    String ServerNALPath[],
    UInt32 Flags[]
);
```

### Parameters

`ServerNALPath` Data type: `String` Array

Qualifiers: \[in\]

Array of network abstraction layer \(NAL\) paths to one or more site system servers.

`Flags` Data type: `UInt32` Array

Qualifiers: \[in\]

Specifies the connection type of the boundary. Possible values are:

| Value | Description |
| --- | --- |
| 0 | FAST |
| 1 | SLOW |

Note

This parameter is no longer used for distribution points.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_DefaultBoundaryGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms-defaultboundarygroup-server-wmi-class)
