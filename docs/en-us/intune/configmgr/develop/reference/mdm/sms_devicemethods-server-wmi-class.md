<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DeviceMethods Server WMI Class

The `SMS_DeviceMethods` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class that provides access to actions that you can take on mobile devices and Microsoft Exchange ActiveSync devices.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DeviceMethods : SMS_Baseclass ();
```

## Methods

The following table shows the methods in `SMS_DeviceMethods`.

| Method | Description |
| --- | --- |
| [AllowAccess Method in Class SMS\_DeviceMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/allowaccess-method-in-class-sms_devicemethods) | Lets the Exchange ActiveSync device connect to Exchange. |
| [BlockAccess Method in Class SMS\_DeviceMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/blockaccess-method-in-class-sms_devicemethods) | Blocks the Exchange ActiveSync device from accessing to Exchange. |
| [NEW SP1: CancelRetire Method in Class SMS\_DeviceMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/cancelretire-method-in-class-sms_devicemethods) | Cancels the retirement of this device from Configuration Manager. |
| [CancelWipe Method in Class SMS\_DeviceMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/cancelwipe-method-in-class-sms_devicemethods) | Cancels a pending wipe request on mobile devices or Exchange ActiveSync devices. |
| [NEW SP1: RequestRetire Method in Class SMS\_DeviceMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/requestretire-method-in-class-sms_devicemethods) | Retires this device from Configuration Manager. |
| [RequestWipe Method in Class SMS\_DeviceMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/requestwipe-method-in-class-sms_devicemethods) | Removes Microsoft Exchange and Configuration Manager software from the mobile device or Exchange ActiveSync device. |

## Properties

The `SMS_DeviceMethods` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Mobile device setting packages use programs, distribution points, and advertisements to collections to distribute their content.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Device Management Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/device-management-server-wmi-classes) [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class)
