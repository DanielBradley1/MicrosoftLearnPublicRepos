<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getcurrentuser-method-in-class-sms_identification -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetCurrentUser Method in Class SMS\_Identification

The `GetCurrentUser` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the domain\\user name that is used by the SMS Provider for authentication.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetCurrentUser(
     String UserName
);
```

#### Parameters

`UserName` Data type: `String`

Qualifiers: \[out\]

Domain\\user name being used by the SMS Provider. This name might differ from the domain\\user name supplied by the application, depending on the domain trust model that is used.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Example Code

The following example shows how to call this method to get the current user.

```
Dim Identification As SWbemObject
Dim UserName As String

Set Identification = GetObject("winmgmts:\root\sms\site_<sitecode>:SMS_Identification")
Identification.GetCurrentUser UserName

MsgBox "UserName = " & UserName
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class)
