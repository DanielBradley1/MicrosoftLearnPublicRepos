<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruledirect-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionRuleDirect Server WMI Class

The `SMS_CollectionRuleDirect` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a resource that is to be made an unconditional member of the collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionRuleDirect : SMS_CollectionRule
{
      String ResourceClassName;
      UInt32 ResourceID;
      String RuleName;
};
```

## Methods

The `SMS_CollectionRuleDirect` class does not define any methods.

## Properties

`ResourceClassName` Data type: ```Strin``g```

Access type: Read/Write

Qualifiers: None

Name of the resource class to which the resource belongs, for example, [SMS\_R\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_system-server-wmi-class). The default value is "".

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the resource that is to become a member of the collection. The default value is 0.

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_CollectionRule Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
