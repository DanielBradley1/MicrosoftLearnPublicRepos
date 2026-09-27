<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_OSConditionGroup Server WMI Class

The `SMS_TaskSequence_OSConditionGroup` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an evaluation of a group of operating system platforms, for example, Windows Vista, in a task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_OSConditionGroup : SMS_TaskSequence_ConditionOperator
{
      SMS_TaskSequence_OSExpressionGroup Operands[];
      String OperatorType;
};
```

## Methods

The `SMS_TaskSequence_OSConditionGroup` class does not define any methods.

## Properties

`Operands` Data type: `SMS_TaskSequence_OSExpressionGroup`Array

Access type: Read/Write

Qualifiers: \[Not\_NULL\]

An array of supported operating system platforms to evaluate. Stored in a

[SMS\_TaskSequence\_OSExpressionGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class) array. There must be at least one array member.

`OperatorType` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_NULL\]

See [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class).

Only the operator "or" is supported.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class) [SMS\_TaskSequence\_OSExpressionGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class)
