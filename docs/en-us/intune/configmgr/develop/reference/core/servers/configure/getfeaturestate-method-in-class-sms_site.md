<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getfeaturestate-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetFeatureState Method in Class SMS\_Site

The `GetFeatureState` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the enabled/disabled state of a feature.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetFeatureState (
     String SiteCode,
     UInt32 FeatureID,
     Boolean IsEnabled
);
```

#### Parameters

`SiteCode` Data type: `String`

Qualifiers: \[in\]

Site code of site to check. NULL indicates the current site.

`FeatureID` Data type: `UInt32`

Qualifiers: \[in\]

Feature identifier. Possible values are:

| Value | Feature |
| --- | --- |
| 1 | SleepServer |

`IsEnabled` Data type: `Boolean`

Qualifiers: \[out\]

`true` if the feature is enabled.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
