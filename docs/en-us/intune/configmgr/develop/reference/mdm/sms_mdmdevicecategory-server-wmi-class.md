<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmdevicecategory-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_MDMDeviceCategory Server WMI Class

The `SMS_MDMDeviceCategory` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an On-premises Mobile Device Management \(MDM\) device category.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMDeviceCategory : SMS_BaseClass
{
    String CategoryID;
    String Name;
};
```

## Methods

The `SMS_MDMDeviceCategory` class does not define any methods.

## Properties

`CategoryID` Data type: `String`

Access type: Read-only

Qualifiers: \[key\]

Category ID.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

Category name.

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
