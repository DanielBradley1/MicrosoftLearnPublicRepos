<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/adddistributionpoints-method-in-class-sms_contentpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddDistributionPoints Method in Class SMS\_ContentPackage

The `AddDistributionPoints` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds the distribution points to the [SMS\_ContentPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_contentpackage-server-wmi-class) content package.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
sint32 AddDistributionPoints (
     string SiteCode[],
     string NALPath[]
);
```

#### Parameters

`SiteCode` Data type: `String` Array

Qualifiers: `[in]`

The code for the site to which to add distribution points.

`NALPath` Data type: `String` Array

Qualifiers: `[in]`

Network abstraction layer \(NAL\) path to the distribution points.

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
