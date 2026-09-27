<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/getavailablelanguages-method-in-class-sms_subscription -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetAvailableLanguages Method in Class SMS\_Subscription

The `GetAvailableLanguages` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the available languages.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 GetAvailableLanguages(
     UInt32 LocaleIDs[]
);
```

#### Parameters

`LocaleIDs` Data type: `UInt32` array

Qualifiers: `[out]`

The identifiers of the locales associated with the localized information.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_Alert server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_alert-server-wmi-class)
