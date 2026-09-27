<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage_driverref-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_BootImagePackage\_DriverRef Server WMI Class

The `SMS_BootImagePackage_DriverRef` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the association between a boot image package and a referenced driver.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_BootImagePackage_DriverRef : SMS_BaseClass
{
     SInt32 CI_ID;
     String PkgID;
     String SourcePath;
};
```

## Methods

The `SMS_BootImagePackage_DriverRef` class doesn't define any methods.

## Properties

`CI_ID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

The unique ID of the configuration item associated with the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object. This ID is unique only for the site. The default value is 0.

`PkgID` Data type: `String`

Access type: Read-only

Qualifiers: \[read, key\]

ID of the boot image package. The default value is "".

`SourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Location of the driver content. The default value is "".

The value of this property is typically the same as the `ContentSourcePath` property for the associated [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object. However, the value can be different if the original content location isn't available.

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  The boot image package is represented by an [SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) object. The drivers contained in the package are indicated in the `ReferencedDrivers` property of this object.

  Your application uses this class to determine what drivers are maintained with the boot image.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_BootImagePackage server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class)
