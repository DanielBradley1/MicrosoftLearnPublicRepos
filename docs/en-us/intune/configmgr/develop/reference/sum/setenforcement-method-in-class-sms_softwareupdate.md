<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/setenforcement-method-in-class-sms_softwareupdate -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetEnforcement Method in Class SMS\_SoftwareUpdate

The `SetEnforcement` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets policy enforcement for the software update.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SetEnforcement(
     Boolean Enforced,
     DateTime EffectiveDate
);
```

#### Parameters

`Enforced` Data type: `Boolean`

Qualifiers: \[in\]

`true` if policy enforcement is enabled for the configuration item.

`EffectiveDate` Data type: `DateTime`

Qualifiers: \[in\]

The date and time, in Coordinated Universal Time \(UTC\), when the configuration item is compliant.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class)
