<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_convertdiskaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_ConvertDiskAction Server WMI Class

The `SMS_TaskSequence_ConvertDiskAction` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that converts a physical disk from a basic disk type to a dynamic disk type.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConvertDiskAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      UInt32 DiskIndex;
      Boolean Enabled;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_ConvertDiskAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("0-255"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`DiskIndex` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Not\_Null, VariableName\("OSDConvertDiskIndex"\)\]

The physical disk number to convert.

The task sequence variable associated with this property is OSDConvertDiskIndex. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("1-100"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

\[CommandLine\("osddiskpart.exe convert %%OSDConvertDiskIndex%%"\),

VariablePrefix\("OSD"\),ActionCategory{"Disks,2,3"},

ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ConvertDiskToDynamicControl", "TaskSequenceOptionControl"}\]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class)
