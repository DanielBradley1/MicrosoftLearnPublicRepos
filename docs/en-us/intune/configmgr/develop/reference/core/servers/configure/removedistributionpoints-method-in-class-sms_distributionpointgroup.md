<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/removedistributionpoints-method-in-class-sms_distributionpointgroup -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RemoveDistributionPoints Method in Class SMS\_DistributionPointGroup

The `RemoveDistributionPoints` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, removes distribution points from this distribution point group.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 RemoveDistributionPoints(
     string DPNALPath[],
     boolean RemoveTargetedPackages
);
```

#### Parameters

`DPNALPath` Data type: `String` Array

Qualifiers: `[in]`

Distribution point NAL path.

`RemoveTargetedPackages` Data type: `Boolean`

Qualifiers: `[in, optional]`

The default value is `false`.

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
