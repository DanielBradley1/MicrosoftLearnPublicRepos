<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addpackages-method-in-class-sms_distributionpointgroup -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddPackages Method in Class SMS\_DistributionPointGroup

The `AddPackages` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, assigns a set of packages to the distribution point group.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 AddPackages(
     string PackageIDs[]
);
```

#### Parameters

`PackageIDs` Data type: `String` Array

Qualifiers: `[in]`

A unique, auto-generated key that is used to relate programs, advertisements, and distribution points to the package.

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
