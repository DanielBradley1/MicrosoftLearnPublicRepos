<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aihardwarerequirements -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSummary Method in Class SMS\_AIHardwareRequirements

The `GetSummary` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, provides a summary count of validated and user-defined state items in the `SMS_AIHardwareRequirements` class.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetSummary(
     UInt32 Validated,
     UInt32 UserDefined
);
```

#### Parameters

`Validated` Data type: `UInt32`

Qualifiers: \[out\]

Count of Microsoft-defined items.

`UserDefined` Data type: `UInt32`

Qualifiers: \[out\]

Count of user-defined items.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_AIHardwareRequirements Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aihardwarerequirements-server-wmi-class)
