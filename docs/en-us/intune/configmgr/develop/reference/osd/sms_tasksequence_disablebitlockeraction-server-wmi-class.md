<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_disablebitlockeraction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_DisableBitLockerAction server WMI class

The `SMS_TaskSequence_DisableBitLockerAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that disables the BitLocker encryption on the specified drive.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_DisableBitLockerAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String Name;
      UInt32 RebootCount;
      String SupportedEnvironment;
      String TargetDrive;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_DisableBitLockerAction` class doesn't define any methods.

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

Qualifiers: `[AllowedLen("0-255")]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `RebootCount`

Data type: `UInt32`

Access type: Read/write

The default value is `1`. Specify the number of restarts to keep BitLocker disabled.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is `FullOS`.

### `TargetDrive`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(1)]`

Drive letter of the volume on which to disable the BitLocker encryption. To use the current OS volume, set this property to `null`.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

```
[CommandLine("OSDBitLocker.exe /disable \<?1: /drive:%1>"),

ActionCategory{"Disks,5,3"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "DisableBitLockerControl", "TaskSequenceOptionControl"}, VariablePrefix("OSDBitLocker")]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class)
