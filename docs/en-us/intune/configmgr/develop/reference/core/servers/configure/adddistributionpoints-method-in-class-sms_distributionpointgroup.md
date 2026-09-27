<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/adddistributionpoints-method-in-class-sms_distributionpointgroup -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddDistributionPoints Method in Class SMS\_DistributionPointGroup

The `AddDistributionPoints` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds distribution points to the distribution point group.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 AddDistributionPoints(
     string DPNALPath[],
     boolean AddTargetedPackages
);
```

#### Parameters

`DPNALPath` Data type: `String` Array

Qualifiers: `[in]`

Distribution point NAL path.

`AddTargetedPackages` Data type: `Boolean`

Qualifiers: `[in, optional]`

`True` if

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
