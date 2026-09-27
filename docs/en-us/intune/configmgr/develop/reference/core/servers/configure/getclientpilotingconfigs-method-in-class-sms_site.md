<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getclientpilotingconfigs-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetClientPilotingConfigs Method in Class SMS\_Site

The `GetClientPilotingConfigs` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the configurations for client piloting settings.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetClientPilotingConfigs (
    Boolean IsEnabled,
    Boolean IsAccepted,
    String TargetCollectionID,
    Datetime LastModifiedTime,
    String LastModifiedBy
);
```

#### Parameters

`IsEnabled` Data type: `Boolean`

Qualifiers: \[out\]

Indicates whether client piloting testing mode is enabled.

`IsAccepted` Data type: `Boolean`

Qualifiers: \[out\]

Indicates whether the new client binaries are accepted. If `IsEnabled` is `true`, this parameter is ignored and is always `false`.

`TargetCollectionID` Data type: `String`

Qualifiers: \[out\]

Targeted collection ID.

`LastModifiedTime` Data type: `Datetime`

Qualifiers: \[out\]

The time that the last modification was made.

`LastModifiedBy` Data type: `String`

Qualifiers: \[out\]

The user name of the user who made the last modification.

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
