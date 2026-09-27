<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/createccr-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# CreateCCR Method in Class SMS\_Collection

The `CreateCCR` Windows Management Instrumentation \(WMI\) class method creates a client configuration request \(CCR\) for a particular resource.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CreateCCR(
     UInt32 ResourceID,
     Boolean PushOnlyAssignedClients,
     SInt32 ClientType,
     Boolean Forced,
     Boolean ForceReinstall,
     Boolean PushEvenIfDC,
     Boolean InformationOnly,
     Boolean SpecifySiteCode,
     String PushSiteCode)
```

#### Parameters

`ResourceID` Data type: `UInt32`

Qualifiers: \[in\]

ID of a member resource.

`PushOnlyAssignedClients` Data type: `Boolean`

Qualifiers: \[in, optional\]

This property is deprecated.

`ClientType` This property is deprecated.

`Forced` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to force installation. This defaults to `false`, if not specified. This is used for force reinstallation, even if the client is already installed. If set to `true`, the operating system is ignored.

`ForceReinstall` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to force reinstallation. The value defaults to false, if not specified.

`PushEvenIfDC` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to push installation on a domain component. The value defaults to false, if not specified.

`InformationOnly` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` if the CCR is for information only. This parameter is only used to gather information from the client. The value defaults to false, if not specified.

`SpecifySiteCode` Data type: `Boolean`

Qualifiers: \[in, optional\]

`SpecifySiteCode` is used to control whether the `PushSiteCode` parameter is used. If `SpecificySiteCode` is set to `true`, `PushSiteCode` is used. If `SpecificySiteCode` isn't set to `true`, `PushSiteCode` won't be used.

`PushSiteCode` Data type: `Boolean`

Qualifiers: \[in, optional\]

`PushSiteCode` defines which site initiates the actual push. The specified site pushes its client files to the client and do the actual installation.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
