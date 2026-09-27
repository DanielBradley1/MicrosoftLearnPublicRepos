<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/adddrivercontent-method-in-class-sms_driverpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddDriverContent Method in Class SMS\_DriverPackage

The `AddDriverContent` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds a driver to the driver package and replicates the driver content to distribution points.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddDriverContent(
     UInt32 ContentIDs[],
     String ContentSourcePath[],
     Boolean bRefreshDPs
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: \[in\]

The IDs for content to add to the driver package.

`ContentSourcePath` Data type: `String` Array

Qualifiers: \[in\]

The source paths where the content files are located. In most cases, these paths should be the same as the settings for the `ContentSourcePath` properties of the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) objects represented by the driver package. The paths can be overridden with local paths if the SMS Provider does not have access to the central site for Configuration Manager.

`bRefreshDPs` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true`, by default, if driver package content is to be replicated to the distribution points.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

An example of the use of this method is provided in [How to Create a Driver Package for a Windows Driver in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-driver-package-for-a-windows-driver).

If the call to this method fails, check the Smsprov.log file on the provider computer for more information.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_DriverPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class) [RemoveDriverContent Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/removedrivercontent-method-in-class-sms_driverpackage) [ValidateNewPackageSource Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage) [How to Create a Driver Package for a Windows Driver in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-driver-package-for-a-windows-driver)
