<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getproviderversion-method-in-class-sms_identification -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetProviderVersion Method in Class SMS\_Identification

The `GetProviderVersion` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the product version string from the version resources of the SMS Provider DLL.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetProviderVersion(
      String VersionString
);
```

#### Parameters

`VersionString` Data type: `String`

Qualifiers: \[out\]

Product version string from the version resources of the Smsprov.dll file.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

The version that is obtained by this method allows your application to determine whether the SMS Provider has had a hotfix applied.

## Example Code

The following example shows how to call this method to get the version number of the SMS Provider.

```
Dim Identification As SWbemObject
Dim ProviderVersion As String

Set Identification = GetObject("winmgmts:\root\sms\site_<sitecode>:SMS_Identification")
Identification.GetProviderVersion ProviderVersion

MsgBox "Version = " & ProviderVersion
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class)
