<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_ConditionOperand Server WMI Class

The `SMS_TaskSequence_ConditionOperand` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager. This class is the abstract base class for operators and expressions that are used by task sequence steps.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConditionOperand
{
};
```

## Methods

The `SMS_TaskSequence_ConditionOperand` class does not define any methods.

## Properties

The `SMS_TaskSequence_ConditionOperand` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- Abstract

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  `SMS_TaskSequence_ConditionOperand` derived classes are used to define condition expressions and operators that determine whether a task sequence step should be run. There are two derived classes.

## SMS\_TaskSequence\_ConditionExpression

[SMS\_TaskSequence\_ConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class) is the base class for an expression that must evaluate to `true` before the step can be processed. For example, the derived class [SMS\_TaskSequence\_RegistryConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_registryconditionexpression-server-wmi-class) defines an expression for the existence of a registry key.

## SMS\_TaskSequence\_ConditionOperator

[SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class) defines a Boolean operator and the expressions that are used to evaluate nested expressions.

These classes can be used to define complex conditions such as `Expression1 and (Expression2 or Expression3)`. For more information, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class) [SMS\_TaskSequence\_ConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class)
