<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getsiteid-method-in-class-sms_identification -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSiteID Method in Class SMS\_Identification

The `GetSiteID` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the unique ID of the installed Configuration Manager site.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetSiteID(
   String SiteID
);
```

#### Parameters

`SiteID` Data type: `String`

Qualifiers: \[out\]

Site ID of the Configuration Manager site.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class)
