<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/verifypackage-method-in-class-sms_distributionpoint -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# VerifyPackage Method in Class SMS\_DistributionPoint

The `VerifyPackage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, verifies the integrity of all the files in the package by calculating the hash of each file.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 VerifyPackage(
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
