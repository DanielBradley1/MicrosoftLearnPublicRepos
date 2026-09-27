<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/unlock-method-in-class-sms_devicesettingpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Unlock Method in Class SMS\_DeviceSettingPackage

The `Unlock` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets the source site to the current site, unlocking the device setting package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 Unlock();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## See Also

[SMS\_DeviceSettingPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackage-server-wmi-class) [RefreshPkgSource Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/refreshpkgsource-method-in-class-sms_devicesettingpackage) [SetSourceSite Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/setsourcesite-method-in-class-sms_devicesettingpackage)
