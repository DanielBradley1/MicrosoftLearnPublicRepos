<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_Group Server WMI Class

The `SMS_Group` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a resource group and serves as the abstract base class for [SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_Group : SMS_BaseClass
{
     UInt32 ResourceID;
};
```

## Methods

The `SMS_Group` class does not define any methods.

## Properties

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Configuration Manager-supplied ID that uniquely identifies a client resource. The default value is 0. This ID is unique only for the site.

Inventory items with the same `ResourceID` property are all found on the same client.

## Remarks

Class qualifiers for this class include:

- Abstract
- Read:ToSubClass

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class)
