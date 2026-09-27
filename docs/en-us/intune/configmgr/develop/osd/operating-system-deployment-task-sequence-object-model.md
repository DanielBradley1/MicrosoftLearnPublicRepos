<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequence-object-model -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Operating System Deployment Task Sequence Object Model

In Configuration Manager, operating system deployment task sequences are created and edited by using a Windows Management Instrumentation \(WMI\) class-based object model.

Caution

Changing task sequences by updating the task sequence XML is not supported. You will only need the XML when exporting the task sequence to different site. The XML is stored in the [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class)`Sequence` property.

## Task Sequence Packages

A task sequence is packaged in an instance of the [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) class and there is a single package for each task sequence. The package is advertised to client computers by using an instance of the [SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) class. To associate the task sequence package with the advertisement, you set the [SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) PackageID property to the [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) PackageID property.

Note

[SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) derives from [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) and can be used in the same way that packages are used. For more information, see [Software distribution overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview).

For more information about creating a task sequence package, see [How to Create an Operating System Deployment Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package).

For more information about creating advertisements, see [How to Create an Advertisement](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-an-advertisement).

## Task Sequences

To create and manage task sequences, Configuration Manager provides a number of WMI classes that represent a task sequence, task sequence steps \(actions and groups\) and step conditions.

The key WMI classes are:

### SMS\_TaskSequence

The [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) class represents an individual task sequence. You can either create new instances of [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class), or you can use the method [SMS\_TaskSequencePackage.GetSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage) to populate an [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) with an existing task sequence.

Note

If you create a new [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class), you must associate it with a [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class). Otherwise, Configuration Manager is not aware of its existence.

The class property SMS\_TaskSequence.Steps is an array of [SMS\_TaskSequence\_Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) derived classes. These steps are processed sequentially when the task sequence is run.

### SMS\_TaskSequenceStep

The two types of steps, action and group, derive from the [SMS\_TaskSequenceStep](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) class. The two types of steps are the [SMS\_TaskSequence\_Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_group-server-wmi-class) class for groups and the [SMS\_TaskSequence\_Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) derived class for the Configuration Manager built-in, or custom, actions.

A step has a number of properties that you can set.

| Property | Description |
| --- | --- |
| Condition | A condition that must be met for the step to be processed. This in an instance of the [SMS\_TaskSequence\_Condition](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class) class. |
| ContinueOnError | If set to `true`, the task sequence will continue to the next step when an error occurs. Otherwise the task sequence will propagate the failure back to the parent. If the parent is a group, the parent group's ContinueOnError property is evaluated. If the parent is the task sequence root, the task sequence will fail. |
| Enabled | If set to `true`, the step is processed. Otherwise, the step is not processed. |

The step also has a Name and Description property.

Note

This documentation refers to steps when the procedure is applicable to both actions and groups. For example, [How to Remove a Step From an Operating System Deployment Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-step-from-an-operating-system-deployment-group) is a task that is applicable to both action removal and group removal.

#### SMS\_TaskSequenceAction

Configuration Manager defines a number of built-in actions that are defined in classes derived from the [SMS\_TaskSequence\_Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) class. For example, the action that allows you to specify a command line is the [SMS\_TaskSequence\_RunCommandLineAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class) class.

Note

The built-in actions are named SMS\_TaskSequence\_`ActionName`Action where `ActionName` is the name of the built-in action. For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

In addition to the properties that are inherited from [SMS\_TaskSequenceStep](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class), a derived action inherits the following properties from the [SMS\_TaskSequence\_Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) class that you can set:

| Property | Description |
| --- | --- |
| SupportedEnvironment | Specifies the operating environment that the action can be run in. Valid values are "WinPE", "FullOS", "WinPEandFullOS. |
| Timeout | Specifies the time-out period for the action, in seconds. |

#### SMS\_TaskSequenceGroup

The [SMS\_TaskSequence\_Group Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_group-server-wmi-class) class represents a set of steps that are processed sequentially. [SMS\_TaskSequence\_Group Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_group-server-wmi-class) Steps property is an array of [SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) classes that represent the group's steps. Because a group step is derived from [SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class), there can be further child groups within the steps.

### SMS\_TaskSequence\_Condition

Each [SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) and the derived classes \(actions and groups\) can have an associated condition that must be met for the condition to be run. For example, you may want to process a step on a computer with Microsoft Office 2007 installed. Additionally, you may also want to further restrict the step to the Windows Vista operating system.

Note

For the condition to be processed, the `SMS_TaskSequenceStep` class `Enabled` property must be set to `true`.

Within a task sequence step, the [SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) Condition property contains a [SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class) object that holds the condition. The condition is made up of one or more operands that are defined in an array of [SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class) derived classes by the `Operands` property. Each operand is an expression that must evaluate to `true`, for the step to be processed - a logical `and` operation.

#### Expressions

Individual expressions are defined in [SMS\_TaskSequence\_ConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class) derived classes.

Note

`SMS_TaskSequence_ConditionExpression` derives from `SMS_TaskSequenceConditionOperand`.

For example, you would use [SMS\_TaskSequence\_SoftwareConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_softwareconditionexpression-server-wmi-class) to define an expression for Microsoft Office 2007. The class used to define an expression for Windows Vista would be [SMS\_TaskSequence\_OSConditionGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class).

#### Nested Expressions

You can define more complex conditions containing nested expressions with [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class). This class also derives from [SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class).

For example, you can form the condition `Exp1 and (Exp2 or Exp3)` by adding the following condition operands to a task sequence step's [SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class) instance's `Operand` array property.

- `SMS_TaskSequence_ConditionExpression` \(`Exp1`\).
- `SMS_TaskSequence_ConditionOperator` \(nested expression `Exp2 or Exp3`\).

  The [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class)`Operands` array property contains the expressions `Exp2` and `Exp3` and the [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class)`Operator` property contains the desired operator. In this case `or`.

Note

The operands in the task sequence step's [SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class)`Operand` array property are automatically compared with the `and` operator to evaluate the condition. The expressions in the `SMS_TaskSequence_ConditionOperator` must have an operator defined by the `Operator` property.

Since the [SMS\_TaskSequence\_Condition Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class)`Operands` property is an array of [SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class) classes, you can create more complex conditions such as `Exp1 and (Exp2 or (Exp3 and Exp4))`.

For more information about conditions, see [How to Add a Condition to an Operating System Deployment Task Sequence Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-condition-to-an-operating-system-deployment-task-sequence-step).

## See Also

[SMS\_TaskSequence\_ConditionOperand Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class) [How to Add a Condition to an Operating System Deployment Task Sequence Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-condition-to-an-operating-system-deployment-task-sequence-step)
