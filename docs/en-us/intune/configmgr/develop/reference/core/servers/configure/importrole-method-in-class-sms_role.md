<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/importrole-method-in-class-sms_role -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ImportRole Method in Class SMS\_Role

The `ImportRole` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, imports a role defined by an XML string to the database.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ImportRole(
     String RolesXml,
     Boolean OverwrittenExisted,
     String ErrorStr,
);
```

#### Parameters

`RolesXml` Data type: `String`

Qualifiers: \[in\]

The id of the role.

`OverwrittenExisted` Data type: `Boolean`

Qualifiers: \[in\]

`true`, if an existing role should be overwritten. The default value is true.

`ErrorStr` Data type: `String`

Qualifiers: \[out\]

The error information if there is any error while importing the role.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Role Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_role-server-wmi-class)
