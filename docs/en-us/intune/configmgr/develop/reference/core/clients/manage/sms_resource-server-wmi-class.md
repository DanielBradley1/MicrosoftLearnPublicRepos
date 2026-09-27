<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resource-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_Resource Server WMI Class

The `SMS_Resource` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that serves as an abstract base class for all discovery resource classes, for example, [SMS\_R\_IPNetwork Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_ipnetwork-server-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_Resource : SMS_BaseClass
{
     UInt32 ResourceID;
};
```

## Methods

The `SMS_Resource` class doesn't define any methods.

## Properties

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: \[key\]

Configuration Manager-supplied ID that uniquely identifies a Configuration Manager client resource. This ID isn't unique across sites. The default value is ''".

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

[SMS\_ResourceMap Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class)
