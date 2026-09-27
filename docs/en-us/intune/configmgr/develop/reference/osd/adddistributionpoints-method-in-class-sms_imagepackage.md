<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/adddistributionpoints-method-in-class-sms_imagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddDistributionPoints Method in Class SMS\_ImagePackage

The `AddDistributionPoints` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds the list of distribution points for the image package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddDistributionPoints(
      String SiteCode[],
      String NALPath[]
);
```

#### Parameters

`SiteCode` Data type: `String` Array

Qualifiers: \[in\]

The code for the site to which to add the distribution points.

`NALPath` Data type: `String` Array

Qualifiers: \[in\]

Network abstraction layer \(NAL\) path to the distribution points.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

It is not necessary to refresh the distribution points when using this method.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagepackage-server-wmi-class)
