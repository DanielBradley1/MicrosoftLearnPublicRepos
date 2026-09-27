<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aisoftwarelist -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSummary Method in Class SMS\_AISoftwareList

The `GetSummary` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, returns a summary count of each of the states defined by the `SMS_AISoftwareList` WMI class records `State` property.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetSummary(
     UInt32 Validated,
     UInt32 UserDefined,
     UInt32 Pending,
     UInt32 Updatable,
     UInt32 Uncategorized
);
```

#### Parameters

`Validated` Data type: `UInt32`

Qualifiers: \[out\]

Count of software titles with the state `Validated`.

`UserDefined` Data type: `UInt32`

Qualifiers: \[out\]

Count of software titles with the state `User Defined`.

`Pending` Data type: `UInt32`

Qualifiers: \[out\]

Count of software titles with the state `Pending`.

`Updatable` Data type: `UInt32`

Qualifiers: \[out\]

Count of software titles with the state `Updatable`.

`Uncategorized` Data type: `UInt32`

Qualifiers: \[out\]

Count of software titles with the state `Uncategorized`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_AISoftwareList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aisoftwarelist-server-wmi-class)
