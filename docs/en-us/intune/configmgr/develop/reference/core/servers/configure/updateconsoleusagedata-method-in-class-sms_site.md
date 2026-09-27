<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/updateconsoleusagedata-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateConsoleUsageData Method in Class SMS\_Site

The `UpdateConsoleUsageData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates console usage data received from console connections.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 UpdateConsoleUsageData (
    SMS_ConsoleUsageData ConsoleUsageData
);
```

#### Parameters

`ConsoleUsageData` Data type: `SMS_ConsoleUsageData`

Qualifiers: \[in\]

Console usage data.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
