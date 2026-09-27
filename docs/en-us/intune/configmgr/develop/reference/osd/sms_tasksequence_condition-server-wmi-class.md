<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_Condition Server WMI Class

The `SMS_TaskSequence_Condition Server WMI Class` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that defines a condition for an operating system deployment step. This class is the base class for all conditions.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_Condition
{
      SMS_TaskSequence_ConditionOperand Operands[];
};
```

## Methods

The `SMS_TaskSequence_Condition` class does not define any methods.

## Properties

`Operands` Data type: `SMS_TaskSequence_ConditionOperand` Array

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

[SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class) objects indicating condition operands. For example, the array can contain a single expression, such as an [SMS\_TaskSequence\_WMIConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class) object. A more complicated condition array can contain a combination of expressions, operators, and operating system condition groups.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

This class is the root for a hierarchy of operator and expression objects that represent the condition that determines whether a step or group or action should be executed. This class implies an AND operator. Therefore, all child operands in the array must be `true` for the overall condition to be `true`.

For example, you might want to process a step on a computer that must have Microsoft Office 2007 and Windows Vista installed. In this case, you add to the `Operands` property array, a [SMS\_TaskSequence\_SoftwareConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_softwareconditionexpression-server-wmi-class) that defines Microsoft Office 2007 and a [SMS\_TaskSequence\_OSConditionGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class) that defines Windows Vista. The overall condition evaluates to `true` only when the two operands are `true`. That is, when Microsoft Office 2007 is installed on a computer with Windows Vista installed.

For more information about conditions, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class) [SMS\_TaskSequence\_WMIConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class)
