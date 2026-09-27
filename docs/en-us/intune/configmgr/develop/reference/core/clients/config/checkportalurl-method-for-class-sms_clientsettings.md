<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/checkportalurl-method-for-class-sms_clientsettings -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CheckPortalUrl Method for Class SMS\_ClientSettings

The `CheckPortalUrl` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, checks whether the default application catalog website point in the default or custom client agent settings is set to `portalUrl`.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 CheckPortalUrl(
     string PortalUrl,
     boolean isUsed
);
```

#### Parameters

`PortalUrl` Data type: `String`

Qualifiers: `[in]`

PortalUrl.

`isUsed` Data type: `Boolean`

Qualifiers: `[out]`

isUsed.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ClientSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientsettings-server-wmi-class)
