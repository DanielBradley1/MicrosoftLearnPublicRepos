<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getadminextendeddata-method-in-class-sms_admin -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetAdminExtendedData Method in Class SMS\_Admin

The `GetAdminExtendedData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the extended data that the current user and its groups have for a given type.

Warning

This method is reserved for internal use.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 GetAdminExtendedData(
    [in] uint32 Type,
    [out] string ExtendedData[]);
};
```

#### Parameters

`Type` Data type: `UInt32`

Qualifiers: \[in\]

The type associated with the user.

`ExtendedData` Data type: `String` Array

Qualifiers: \[out\]

The extended data that the current user and its groups have for a given type.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Admin Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_admin-server-wmi-class)
