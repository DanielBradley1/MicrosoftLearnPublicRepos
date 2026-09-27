<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/redistributeautoupgradeclientcontent-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RedistributeAutoUpgradeClientContent Method in Class SMS\_Site

The `RedistributeAutoUpgradeClientContent` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, redistributes auto-upgrade client content to the specified distribution point.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RedistributeAutoUpgradeClientContent(
     String DPNALPath
);
```

#### Parameters

`DPNALPath` Data type: `String`

Qualifiers: \[in\]

Distribution point NAL path.

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
