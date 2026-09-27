<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/importglobaluseraccount-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ImportGlobalUserAccount Method in Class SMS\_Site

The `ImportGlobalUserAccount` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, encrypts data that is shared in the hierarchy.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ImportGlobalUserAccount(
     String UserName,
     UInt8 Password[]
);
```

#### Parameters

`UserName` Data type: `String`

Qualifiers: \[in\]

Name of the user account to import.

`Password` Data type: `Uint8` Array

Qualifiers: \[in\]

Password.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
