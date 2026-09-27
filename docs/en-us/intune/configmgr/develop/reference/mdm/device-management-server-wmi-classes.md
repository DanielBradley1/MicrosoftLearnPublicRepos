<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/device-management-server-wmi-classes -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Configuration Manager Device Management Server WMI Classes

Device management server Windows Management Instrumentation \(WMI\) classes in Configuration Manager assist in assessment of computer compliance considering a number of mobile device configurations.

The Configuration Manager server class schema is a set of WMI classes that represent the objects found on a server that is running Configuration Manager. Each Configuration Manager class is a template for a managed object and all instances of the object use the template. Classes can contain properties and methods. The properties describe the class data and the methods typically perform data management. For more information about developing applications using these classes, see [About Configuration Manager SDK Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/about-configuration-manager-sdk-requirements).

## Mobile Device Management Classes

- [SMS\_DeviceEnrollmentProfile Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_deviceenrollmentprofile-server-wmi-class)
- [SMS\_DeviceMethods Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class)
- [SMS\_DeviceSettingItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingitem-server-wmi-class)
- [SMS\_DeviceSettingPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackage-server-wmi-class)
- [SMS\_DeviceSettingPackageItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackageitem-server-wmi-class)

## Remarks

Configuration Manager uses its device management functionality for mobile devices. It uses a special type of configuration item to represent a set of mobile device settings to apply to a mobile device. The device setting configuration item can only be distributed by using a device setting package that is accessible in the Configuration Package wizard in the Configuration Manager console. Source locations are defined automatically when creating the package.

Note

Mobile devices do not have domain accounts and therefore do not recognize access account restrictions.

## See Also

[Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
