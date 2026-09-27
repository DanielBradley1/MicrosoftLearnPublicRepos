<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/setsourcesite-method-in-class-sms_advertisement -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetSourceSite Method in Class SMS\_Advertisement

The `SetSourceSite` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets the source site code for the advertisement.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 SetSourceSite(
     string SourceSite,
);
```

#### Parameters

`SourceSite` Data type: `String`

Qualifiers: `[in]`

The site code of the source site for the advertisement.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class)
