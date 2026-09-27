<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_SetVariableAction server WMI class

The `SMS_TaskSequence_SetVariableAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that sets the value of a task sequence environment variable.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_SetVariableAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean DoNotShowVariableValue;
      Boolean Enabled;
      string HiddenVariableValue;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
      String VariableName;
      String VariableValue;
};
```

## Methods

The `SMS_TaskSequence_SetVariableAction` class doesn't define any methods.

## Properties

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

Qualifiers: \[AllowedLen\("0-255"\)\]

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `DoNotShowVariableValue`

Data type: `Boolean`

Access type: Read/write

Default value `false`. This property corresponds to the setting in the task sequence editor, **Do not display this value**.

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `HiddenVariableValue`

Data type: `String`

Access type: Read/write

Hidden value of the task sequence environment variable. The value length must be between 0 and 4,001 characters.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("1-100"\)\]

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `VariableName`

Data type: `String`

Access type: Read/Write

Qualifiers: \[CommandLineArg\(1\), Not\_Null, AllowedLen\("1-256"\)\]

Name of the task sequence environment variable to set. The name length must be between 1 and 256 characters.

### `VariableValue`

Data type: `String`

Access type: Read/Write

Qualifiers: \[CommandLineArg\(2\), Not\_Null, AllowedLen\("0-4001"\)\]

Value of the task sequence environment variable. The value length must be between 0 and 4,001 characters.

## Remarks

Class qualifiers for this class include:

```
[CommandLine("tsenv.exe \\"%1=%2\\""),

ActionCategory{"General,7,1"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "SetSequenceVariableControl", "TaskSequenceOptionControl"}]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
