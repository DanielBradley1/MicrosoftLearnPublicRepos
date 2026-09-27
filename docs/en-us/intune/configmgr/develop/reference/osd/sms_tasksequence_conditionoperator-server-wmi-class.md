<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_ConditionOperator Server WMI Class

The `SMS_TaskSequence_ConditionOperator` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an operator to use when evaluating task sequence condition operands.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConditionOperator : SMS_TaskSequence_ConditionOperand
{
      SMS_TaskSequence_ConditionOperand Operands[];
      String OperatorType;
};
```

## Methods

The `SMS_TaskSequence_ConditionOperator` class does not define any methods.

## Properties

`Operands` Data type: `SMS_TaskSequence_ConditionOperand` Array

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

[SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class) objects to test.

`OperatorType` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

Type of operator to use in testing the conditions. Possible values are:

- and
- or
- not

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

Note

Task sequence step conditions are defined in [SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class).

`SMS_TaskSequence_ConditionOperator` is used to create complete complex conditions that determine if a task sequence step should be processed. The `Operands` array property holds one or more expression \([SMS\_TaskSequence\_ConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class)\) or operator \(`SMS_TaskSequence_ConditionOperator`\) operands to evaluate.

Note

Both of these classes derive from SMS[SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class), the type for the `Operands` property.

The operator used to evaluate the operands is defined by the `OperatorType` property.

For more information, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence\_ConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class) [SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class) [SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class)
