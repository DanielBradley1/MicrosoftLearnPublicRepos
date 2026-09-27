<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_prepareosaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_PrepareOSAction server WMI class

The `SMS_TaskSequence_PrepareOSAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that specifies the Sysprep options to use when capturing Windows settings from the reference computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_PrepareOSAction : SMS_TaskSequence_Action
{
      Boolean BuildStorageDriverList;
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      Boolean KeepActivation;
      String Name;
      boolean ShutdownPreparedOs;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_PrepareOSAction` class doesn't define any methods.

## Properties

### `BuildStorageDriverList`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[not_null, VariableName("OSDBuildStorageDriverList")]`

Set `true` to build a mass-storage device driver list. The default value is `false`.

This property is deprecated. It only applies to Windows XP and Windows Server 2003.

### `Condition`

Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `ContinueOnError`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Description`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("0-255")]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `KeepActivation`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[not_null, VariableName("OSDKeepActivation")]`

Set `true` to keep the current product activation flag. Set `false` to reset it. The default value is `false`.

The task sequence variable associated with this property is [OSDKeepActivation](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables#OSDKeepActivation).

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `ShutdownPreparedOs`

Data type: `Boolean`

Access type: Read/write

Corresponds to the following setting in the task sequence editor: **Shutdown the computer after running this action**. The default value is `false`.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is `FullOS`.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

```
[CommandLine("osdprepareos.exe /activate:%%OSDKeepActivation%% /bmsd:%%OSDBuildStorageDriverList%%"),

ActionCategory{"Images,7,5"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "WindowsCaptureControl", "TaskSequenceOptionControl"}]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
