<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/setsourcesite-method-in-class-sms_devicesettingpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetSourceSite Method in Class SMS\_DeviceSettingPackage

The `SetSourceSite` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets the code of the source site for the device setting package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SetSourceSite(
   String SourceSite
);
```

#### Parameters

`SourceSite` Data type: `String`

Qualifiers: \[in\]

The code of the source site for the device setting package.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## See Also

[SMS\_DeviceSettingPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackage-server-wmi-class) [RefreshPkgSource Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/refreshpkgsource-method-in-class-sms_devicesettingpackage)
