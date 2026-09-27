<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackageitem-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DeviceSettingPackageItem Server WMI Class

The `SMS_DeviceSettingPackageItem` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that associates a device setting configuration item with a device setting package.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DeviceSettingPackageItem : SMS_BaseClass
{
      String DeviceSettingItemUniqueID;
      String PackageID;
};
```

## Methods

The `SMS_DeviceSettingPackageItem` class doesn't define any methods.

## Properties

`DeviceSettingItemUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

GUID or unique ID for the [SMS\_DeviceSettingItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingitem-server-wmi-class) object that is contained in the [SMS\_DeviceSettingPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackage-server-wmi-class) object represented by `PackageID`. The default value is "".

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID of the [SMS\_DeviceSettingPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackage-server-wmi-class) object that contains the item represented by `DeviceSettingItemUniqueID`. The default value is "".

## Remarks

Class qualifiers for this class include:

- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Device Management Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/device-management-server-wmi-classes) [SMS\_DeviceSettingItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingitem-server-wmi-class) [SMS\_DeviceSettingPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackage-server-wmi-class)
