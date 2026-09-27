<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/initiateuserinstall-method-in-class-sms_application -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# InitiateUserInstall Method in Class SMS\_Application

Warning

This method is reserved for future use.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 InitiateUserInstall (
     String  ModelName,
     String  Username,
     String  ClientGUID
);
```

#### Parameters

`ModelName` Data type: `String`

Qualifiers: \[in\]

Model name of the application.

`Username` Data type: `String`

Qualifiers: \[in\]

Unique user name.

`ClientGUID` Data type: `String`

Qualifiers: \[in\]

Unique identifier of a client.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class)
