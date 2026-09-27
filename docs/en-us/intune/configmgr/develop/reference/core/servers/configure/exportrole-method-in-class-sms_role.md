<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/exportrole-method-in-class-sms_role -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ExportRole Method in Class SMS\_Role

The `ExportRole` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, exports roles to an XML string.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ExportRole(
     String RoleID,
     String ExportedXML,
);
```

#### Parameters

`RoleID` Data type: `String`

Qualifiers: \[in\]

The id of the role.

`ExportedXML` Data type: `String`

Qualifiers: \[out\]

The XML blob for the role.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Role Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_role-server-wmi-class)
