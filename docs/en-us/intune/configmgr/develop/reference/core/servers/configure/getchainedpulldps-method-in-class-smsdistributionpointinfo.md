<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getchainedpulldps-method-in-class-smsdistributionpointinfo -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# GetChainedPullDPs Method in Class SMSDistributionPointInfo

The `GetChainedPullDPs` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, ensures that when a source distribution point is assigned, a looping chain isn't generated. \(If distribution point 1 is the source of distribution point 2, and distribution point 2 is the source of distribution point 3, then distribution point 3 can't be source of distribution point 1\).

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 GetChainedPullDPs(
     string SourceDPNALPath,
     string ChainedDPs[]
);
```

#### Parameters

`SourceDPNALPath` Data type: `String`

Qualifiers: `[in]`

Source distribution point NAL path.

`ChainedDPs` Data type: `String` Array

Qualifiers: `[out]`

An array of chained distribution points.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class)
