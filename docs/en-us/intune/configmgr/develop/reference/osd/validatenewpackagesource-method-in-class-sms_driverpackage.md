<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ValidateNewPackageSource Method in Class SMS\_DriverPackage

The `ValidateNewPackageSource` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, validates a new location for a driver update.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ValidateNewPackageSource(
     String PackageSource
);
```

#### Parameters

`PackageSource` Data type: `String`

Qualifiers: \[in\]

The driver package content to verify.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method is new in the latest version of Configuration Manager. Note that it is the only way to change the package source for an [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object. Most other types of packages can be changed in the console, but not the driver package. The access to this package from the console is restricted.

To use this method:

1. Manually copy the package files from the old source location to the new location.
2. In your application, obtain an [SMS\_DriverPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class) object for the driver.
3. Include a call to `ValidateNewPackageSource` on the package.
4. On successful return from the method, have the application change the `StoredPkgPath` property in the package to indicate the new source location.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_DriverPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class) [RebuildPackage Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/rebuildpackage-method-in-class-sms_driverpackage)
