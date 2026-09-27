<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/generateccrbyname-method-in-class-sms_collecton -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GenerateCCRByName Method in Class SMS\_Collecton

The `GenerateCCRByName` Windows Management Instrumentation \(WMI\) class method generates a client configuration request by computer name.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GenerateCCRByName(
     String Name
     String PushSiteCode
     Boolean Forced
);
```

#### Parameters

`Name` Data type: `String`

Qualifiers: \[in\]

Name of the computer.

`PushSiteCode` Data type: `String`

Qualifiers: \[in\]

PushSiteCode defines which site will initiate the actual push. The specified site will push its client files to the client and do the actual installation.

`Forced` Data type: `Boolean`

Qualifiers: \[in\]

`true` to force installation. The value defaults to false, if not specified.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
