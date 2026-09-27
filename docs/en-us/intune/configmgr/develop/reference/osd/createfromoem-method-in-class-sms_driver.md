<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/createfromoem-method-in-class-sms_driver -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CreateFromOEM Method in Class SMS\_Driver

The `CreateFromOEM` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, creates a set of mass-storage [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) objects referenced by the specified Txtsetup.oem file.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CreateFromOEM(
      String DriverPath,
      String OEMFile,
      SMS_Driver Drivers[]
);
```

#### Parameters

`DriverPath` Data type: `String`

Qualifiers: \[in\]

Universal Naming Convention \(UNC\) path containing the driver content.

`OEMFile` Data type: `String`

Qualifiers: \[in\]

Relative path of the Txtsetup.oem file.

`Drivers` Data type: `SMS_Driver Array`

Qualifiers: \[out\]

An array of drivers with a complete driver catalog.

## Return Values

An `SInt32` data type that is 0 to indicate success or nonzero to indicate failure. The error values are available in the [SMS\_ExtendedStatus Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_extendedstatus-server-wmi-class) error object. For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

This method returns successfully if at least one of the files referenced by the Txtsetup.oem file is valid.

Possible error values include, but aren't limited to, the following:

0 Success

13 The Txtsetup.oem file is invalid.

All drivers referenced by the Txtsetup.oem file are invalid.

2 The SMS provider can't access the Txtsetup.oem file.

1633 All drivers referenced by the Txtsetup.oem file are valid but don't support any platforms supported by Configuration Manager.

183 All drivers referenced by the Txtsetup.oem file have already been imported.

All drivers referenced by the Txtsetup.oem file have another type of error. See the OSDDriverCatalog.log file on the provider computer for more information.

## Remarks

To support pre-Windows Vista operating system deployments, Configuration Manager uses boot-critical mass storage device drivers. This type of driver is furnished in the form of a Txtsetup.oem file supplied on a disk. The file contains the following information:

- Hardware components supported by the file
- Files to copy from the distribution disk for each component
- Registry keys and values to create for each component

  A mass storage device driver file must be installed before setup on a pre-Windows Vista operating system deployment.

Note

Your application should create a driver only by calling this method or the [CreateFromINF Method in Class SMS\_Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/createfrominf-method-in-class-sms_driver). It should never create a driver directly.

Your application calls this method with a driver Txtsetup.oem file and file path. The method examines the supplied information and creates an array of new [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) objects, one for each referenced .inf file.

This method generates [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) objects with System Definition Model \(SDM\) package XML defined, and allows your application to make property changes before they're saved.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)
