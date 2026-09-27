<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/updateautoupgradeconfigs-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# UpdateAutoUpgradeConfigs Method in Class SMS\_Site

The `UpdateAutoUpgradeConfigs` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates configurations for autoupgrade settings.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 UpdateAutoUpgradeConfigs(
     String ClientVersion,
     Boolean IsProgramEnabled,
     UInt32 AdvertisementDuration,
     UInt32 ValidationInterval,
     UInt32 ValidationFailureInterval,
     Boolean AllowPrestage,
     Boolean AllowFallbackToContentSource,
     UInt32 DownloadOptionsInSlowNetwork,
     Boolean ExcludeServers,
     Boolean OverrideServiceWindow,
     Boolean IgnoreNonPersistableVM
);
```

#### Parameters

`ClientVersion` Data type: `String`

Qualifiers: \[in\]

The version of the client.

`IsProgramEnabled` Data type: `Boolean`

Qualifiers: \[in\]

`true` if the program is enabled.

`AdvertisementDuration` Data type: `UInt32`

Qualifiers: \[in\]

Advertisement duration in days.

`ValidationInterval` Data type: `UInt32`

Qualifiers: \[in\]

Validation interval in hours, if the previous validation is successful.

`ValidationFailureInterval` Data type: `UInt32`

Qualifiers: \[in\]

Validation interval in hours, if the previous validation is failed.

`AllowPrestage` Data type: `Boolean`

Qualifiers: \[in\]

`true` if autoupgrade package distributed to pre-stage distribution point is allowed.

`AllowFallbackToContentSource` Data type: `Boolean`

Qualifiers: \[in\]

`true` if fallback to content source is allowed.

`DownloadOptionInSlowNetwork` Data type: `UInt32`

Qualifiers: \[in\]

Download options in slow network. Possible values are:

| Value | Download option |
| --- | --- |
| 0 | Do not download. |
| 1 | Download from distribution point and run locally. |
| 2 | Run from distribution point. |

`ExcludeServers` Data type: `Boolean`

Qualifiers: \[in\]

Indicates whether autoupgrade should be skipped on servers.

`OverrideServiceWindow` Data type: `Boolean`

Qualifiers: \[in\]

Indicates whether the upgrade on the client occurs in service window.

`IgnoreNonPersistableVM` Data type: `Boolean`

Qualifiers: \[in\]

Indicates whether autoupgrade should be skipped on non-persistent virtual machines.

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
