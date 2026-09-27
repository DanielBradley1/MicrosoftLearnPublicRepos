<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruleincludecollection-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionRuleIncludeCollection Server WMI Class

The `SMS_CollectionRuleIncludeCollection` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an inclusion rule that's added as a rule to the `SMS_Collection` instance. Any members of a collection defined by this rule will be included in the collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ CollectionRuleIncludeCollection : SMS_BaseClass
{
      String IncludeCollectionID;
      String RuleName;
};
```

## Methods

The `SMS_ CollectionRuleIncludeCollection` class doesn't define any methods.

## Properties

`IncludeCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: None

The ID of the collection to include in the membership results.

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_CollectionRule Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Abstract

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
