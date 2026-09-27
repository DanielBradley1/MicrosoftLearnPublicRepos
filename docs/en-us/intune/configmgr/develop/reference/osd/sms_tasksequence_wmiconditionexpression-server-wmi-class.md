<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_WMIConditionExpression Server WMI Class

The `SMS_TaskSequence_WMIConditionExpression` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a condition expression to check for the existence of results of a WMI query.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_WMIConditionExpression : SMS_TaskSequence_ConditionExpression
{
      String Namespace;
      String Query;
};
```

## Methods

The `SMS_TaskSequence_WMIConditionExpression` class does not define any methods.

## Properties

`Namespace` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

Namespace for the query.

`Query` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null, AllowedLen\("1-16384"\)\]

The WQL query for the condition expression. The length is between 1 and 16,384 characters.

## Remarks

The query result set is the results that satisfy the condition. For example, if you need to identify if a computer has at least one NTFS partition, you would use the following query:

```
Select * from win32_logicaldisk where FileSystem='NTFS'
```

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
