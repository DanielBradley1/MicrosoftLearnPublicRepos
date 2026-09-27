<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/createfrominf-method-in-class-sms_driver -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CreateFromINF Method in Class SMS\_Driver

The `CreateFromINF` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, creates an [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object based on information from the specified Microsoft Windows .inf file.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CreateFromINF(
      String DriverPath,
      String INFFile,
      SMS_Driver Driver
);
```

#### Parameters

`DriverPath` Data type: `String`

Qualifiers: \[in\]

Valid Universal Naming Convention \(UNC\) network path to the folder that contains the driver contents. For example, \\\\Servers\\Driver\\VideoDriver.

`INFFile` Data type: `String`

Qualifiers: \[in\]

The name of the INF file.

`Driver` Data type: `SMS_Driver`

Qualifiers: \[out\]

An [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object with a complete driver catalog.

## Return Values

An `SInt32` data type that is 0 to indicate success or nonzero to indicate failure. The error values are available in the [SMS\_ExtendedStatus Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_extendedstatus-server-wmi-class) error object. For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

Possible error values include, but aren't limited to, the following:

0 Success

13 The driver is invalid

1633 The driver is valid but doesn't support any platforms supported by Configuration Manager.

2 The SMS Provider can't access the network share.

183 The driver has already been imported.

To find out specifics of an error, see the OSDDriverCatalog.log file.

## Remarks

A driver is represented by an information file \(INF\). The INF file is a text file that specifies the files that need to be present or downloaded for the operating system to run. The information in this type of file provides installation instructions that the Internet Component Download service provided in Microsoft Internet Explorer 3.0 or later uses to install and register software components that are downloaded from the Internet, in addition to any files required by the components.

Note

Your application should create a driver only by calling this method or the [CreateFromOEM Method in Class SMS\_Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/createfromoem-method-in-class-sms_driver). It should never create a driver directly.

This method creates a new [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object.

Once created, the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)`SDMPackageXML` contains the driver definition XML. To set the display information used by the Configuration Manager console for the driver, you need to set the localization information in the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)`LocalizedInformation` property. The driver name used by the display from is available in [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)`SDMPackageXML` property XML. For more information, see How to Import a Windows Driver Described by an INF File into Configuration Manager.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)
