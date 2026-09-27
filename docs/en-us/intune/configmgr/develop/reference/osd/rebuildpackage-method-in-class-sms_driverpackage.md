<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/rebuildpackage-method-in-class-sms_driverpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RebuildPackage Method in Class SMS\_DriverPackage

The `RebuildPackage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, restores the contents for the driver package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RebuildPackage(
     String ContentSourcePath
);
```

#### Parameters

`ContentSourcePath` Data type: `String`

Qualifiers: \[in, optional\]

Source path where the content files are located.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_DriverPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class) [AddDriverContent Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/adddrivercontent-method-in-class-sms_driverpackage) [RemoveDriverContent Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/removedrivercontent-method-in-class-sms_driverpackage) [ValidateNewPackageSource Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage)
