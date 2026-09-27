<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_ConditionExpression Server WMI Class

The `SMS_TaskSequence_ConditionExpression` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that is the abstract base class for all condition expressions.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConditionExpression : SMS_TaskSequence_ConditionOperand
{
};
```

## Methods

The `SMS_TaskSequence_ConditionExpression` class does not define any methods.

## Properties

The `SMS_TaskSequence_ConditionExpression` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- Abstract

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  `SMS_TaskSequence_ConditionExpression` is the abstract base class for an expression that must evaluate to `true`, for the task sequence step to be processed. For example, the derived class [SMS\_TaskSequence\_RegistryConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_registryconditionexpression-server-wmi-class) defines an expression for the existence of a registry key.

  An `SMS_TaskSequence_ConditionExpression` is stored in a condition's \([SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class)\) `Operands` array property, which defines the list of condition operands.

Note

In a task sequence step \([SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class)\), the condition is defined in the `Condition` property.

Alternatively, more complex conditions are created by adding a [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class) object to the condition's `Operands` array property, and by adding expressions and operators to the added [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class)`Operands` array.

For more information, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class) [SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class) [SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class)
