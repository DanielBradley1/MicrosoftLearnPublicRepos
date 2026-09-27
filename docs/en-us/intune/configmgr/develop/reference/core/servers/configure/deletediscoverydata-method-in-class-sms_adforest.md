<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/deletediscoverydata-method-in-class-sms_adforest -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DeleteDiscoveryData Method in Class SMS\_ADForest

The `DeleteDiscoveryData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, removes information gathered by the forest discovery process.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 DeleteDiscoveryData(
     UInt32 ForceDelete
);
```

#### Parameters

`ForceDelete` Data type: `UInt32`

Qualifiers: `[in]`

Delete discovered data. Possible values are:

| Value | Delete data |
| --- | --- |
| 0 | Delete all discovered data excluding forest name and forest properties information. |
| 1 | Delete all data including forest name and forest properties information. |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_ADForest server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_adforest-server-wmi-class)
