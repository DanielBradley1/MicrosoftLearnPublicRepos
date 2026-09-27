<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/close-method-in-class-sms_epalert -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Close Method in Class SMS\_EPAlert

The `Close` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, postpones the alert.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 Close(
     string Comments,
     datetime SkipUntil
);
```

#### Parameters

`Comments` Data type: `String`

Qualifiers: `[in, optional]`

Administrator-supplied comments for the postpone action.

`SkipUntil` Data type: `DateTime`

Qualifiers: `[out, optional]`

Don't start the evaluation until the specified time.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_Alert server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_alert-server-wmi-class)
