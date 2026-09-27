<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/fallbackdp-method-in-class-sms-boundarygrouprelationships -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# FallbackDP Method in Class SMS\_BoundaryGroupRelationships

The `FallbackDP` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets the fallback time, in minutes, for a distribution point \(DP\). The default value is 120.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 FallbackDP();
```

### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BoundaryGroupRelationships Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms-boundarygrouprelationships-server-wmi-class)
