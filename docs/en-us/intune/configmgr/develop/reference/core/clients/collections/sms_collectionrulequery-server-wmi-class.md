<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrulequery-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionRuleQuery Server WMI Class

The `SMS_CollectionRuleQuery` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a member of a collection based on the results of a query.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionRuleQuery : SMS_CollectionRule
{
      String QueryExpression;
      UInt32 QueryID;
      String RuleName;
};
```

## Methods

The following table lists the methods in the `SMS_CollectionRuleQuery` class.

| Method | Description |
| --- | --- |
| [ValidateQuery Method in Class SMS\_CollectionRuleQuery](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery) | Validates the collection rule query. |

## Properties

`QueryExpression` Data type: `String`

Access type: Read/Write

Qualifiers: None

WQL SELECT statement having results that are used to populate the collection. The statement must specify a resource class name. The default value is "".

Your application can use the `LimitToCollectionID` property to further limit the results. Note that the SMS Provider might alter the text of the query to make it more amenable to collection evaluation.

`QueryID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Auto-generated ID that is only useful when deleting a rule.

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
