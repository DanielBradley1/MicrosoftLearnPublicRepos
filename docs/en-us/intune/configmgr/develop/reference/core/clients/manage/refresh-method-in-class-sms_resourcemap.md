<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/refresh-method-in-class-sms_resourcemap -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Refresh Method in Class SMS\_ResourceMap

The `Refresh` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates resource \(classes derived from [SMS\_R\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_system-server-wmi-class)\) and inventory \(classes derived from [SMS\_G\_System\_Current Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class)\) class definitions.

The following syntax is simplified from Manage Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 Refresh();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ResourceMap Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class)
