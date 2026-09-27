<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/updateclientpilotingconfigs-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateClientPilotingConfigs Method in Class SMS\_Site

The `UpdateClientPilotingConfigs` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates the configurations for client piloting settings.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 UpdateClientPilotingConfigs (
    Boolean IsEnabled,
    Boolean IsAccepted,
    String TargetCollectionID
);
```

#### Parameters

`IsEnabled` Data type: `Boolean`

Qualifiers: \[in\]

Indicates whether client piloting testing mode is enabled.

`IsAccepted` Data type: `Boolean`

Qualifiers: \[in\]

Indicates whether the new client binaries are accepted. If `IsEnabled` is `true`, this parameter is ignored and is always `false`.

`TargetCollectionID` Data type: `String`

Qualifiers: \[in\]

Targeted collection ID.

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
