<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/setisexpired-method-in-class-sms_application -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetIsExpired Method in Class SMS\_Application

The `SetIsExpired` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets the expired status of this application.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 SetIsExpired (
     boolean Expired
);
```

#### Parameters

`Expired` Data type: `Boolean`

Qualifiers: \[in\]

`true` to set the state to expired, otherwise, `false`. The default value is `true`.

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
