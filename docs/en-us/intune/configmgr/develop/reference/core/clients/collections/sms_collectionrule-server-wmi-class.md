<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionRule Server WMI Class

The `SMS_CollectionRule` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a collection rule in a collection and serves as an abstract base class for [SMS\_CollectionRuleDirect Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruledirect-server-wmi-class) and [SMS\_CollectionRuleQuery Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrulequery-server-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionRule
{
      String RuleName;
};
```

## Methods

The `SMS_CollectionRule` class does not define any methods.

## Properties

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Descriptive name that identifies the rule. The default value is "".

## Remarks

Class qualifiers for this class include:

- Abstract
- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
