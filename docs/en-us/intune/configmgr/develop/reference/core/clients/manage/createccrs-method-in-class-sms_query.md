<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/createccrs-method-in-class-sms_query -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CreateCCRs Method in Class SMS\_Query

The `CreateCCRs` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, generates client configuration requests \(CCRs\) for the query.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
SInt32 CreateCCRs(
   Boolean PushOnlyAssignedClients,
   SInt32 ClientType,
   Boolean Forced,
   Boolean ForceReinstall,
   Boolean PushEvenIfDC,
   Boolean InformationOnly,
   Boolean SpecifySiteCode,
   String PushSiteCode
);
```

#### Parameters

`PushOnlyAssignedClients` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to push installation only to assigned clients.

`ClientType` Data type: `SInt32`

Qualifiers: \[in, optional\]

Type of client.

`Forced` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to force installation. The value defaults to `false`, if not specified. This is used to force reinstallation, even if the client is already installed. If `Forced` is set to `true`, the operating system value will be ignored.

`ForceReinstall` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to force reinstallation. The value defaults to `false`, if not specified.

`PushEvenIfDC` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` to push installation on a domain component.

`InformationOnly` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` if the CCRs are for information only. This parameter is only used to gather information from the client.

`SpecifySiteCode` Data type: `Boolean`

Qualifiers: \[in, optional\]

`SpecifySiteCode` is used to control whether the `PushSiteCode` parameter is used. The `PushSiteCode` value will not be used unless `SpecificySiteCode` is set to `true`.

`PushSiteCode` Data type: `String`

Qualifiers: \[in, optional\]

`PushSiteCode` defines which site will initiate the actual push. The specified site will push its client files to the client and do the actual installation.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Query Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class)
