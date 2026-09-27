<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/createccrs-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# CreateCCRs Method in Class SMS\_Collection

The `CreateCCRs` WMI class method, in Configuration Manager, generates client configuration requests \(CCRs\) for the computers in the collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CreateCCRs(
     Boolean IncludeSubCollections,
     Boolean PushOnlyAssignedClients,
     SInt32 ClientType,
     Boolean Forced,
     Boolean ForceReinstall,
     Boolean PushEvenIfDC,
     Boolean InformationOnly
     Boolean SpecifySiteCode,
     String PushSiteCode)
);
```

#### Parameters

`IncludeSubCollections` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to include subcollections. This value defaults to false, if not specified.

`PushOnlyAssignedClients` Data type: `Boolean`

Qualifiers: \[in, optional\]

This property is deprecated.

`ClientType` This property is deprecated.

`Forced` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to force installation. This defaults to false, if not specified. This is used for force reinstallation, even if the client is already installed. If set to `true`, the operating system is ignored.

`ForceReinstall` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to force reinstallation. This defaults to false, if not specified.

`PushEvenIfDC` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to push installation on a domain component. This defaults to false, if not specified.

`InformationOnly` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` if the CCRs are for information only. This parameter is only used to gather information from the client. This defaults to false, if not specified.

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
