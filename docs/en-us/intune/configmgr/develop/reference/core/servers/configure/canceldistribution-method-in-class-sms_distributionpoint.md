<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/canceldistribution-method-in-class-sms_distributionpoint -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# CancelDistribution Method in Class SMS\_DistributionPoint

The `CancelDistribution` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, cancels a package distribution. If there's a distribution in-progress for the specified package to the specified distribution point, then calling this method cancels the ongoing distribution and the status of the package distribution will be set to fail for this distribution point.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 CancelDistribution(
     string PackageId,
     string NALPath
);
```

#### Parameters

`PackageId` Data type: `String`

Qualifiers: `[in]`

ID for an existing package.

`NALPath` Data type: `String`

Qualifiers: `[in]`

Network abstraction layer \(NAL\) path to the distribution point server.

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
