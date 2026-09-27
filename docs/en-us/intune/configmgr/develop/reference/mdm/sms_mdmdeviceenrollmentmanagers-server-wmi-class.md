<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmdeviceenrollmentmanagers-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_MDMDeviceEnrollmentManagers Server WMI Class

The `SMS_MDMDeviceEnrollmentManagers` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents On-premises Mobile Device Management \(MDM\) device enrollment managers.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMDeviceEnrollmentManagers : SMS_BaseClass
{
    UInt32 ResourceID;
};
```

## Methods

The following table lists the methods in the `SMS_MDMDeviceEnrollmentManagers` class.

| Method | Description |
| --- | --- |
| [InsertMultipleResourceIds Method in Class SMS\_MDMDeviceEnrollmentManagers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/insertmultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers) | Inserts multiple resource IDs. |
| [RemoveMultipleResourceIds Method in Class SMS\_MDMDeviceEnrollmentManagers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/removemultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers) | Deletes multiple resource IDs. |

## Properties

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Resource ID.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
