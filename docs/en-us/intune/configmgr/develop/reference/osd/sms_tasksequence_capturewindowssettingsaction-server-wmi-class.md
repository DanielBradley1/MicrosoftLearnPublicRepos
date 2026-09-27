<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_capturewindowssettingsaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_CaptureWindowsSettingsAction Server WMI Class

The `SMS_TaskSequence_CaptureWindowsSettingsAction` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that identifies the settings of the Windows operating system to capture from the target computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_CaptureWindowsSettingsAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      Boolean MigrateComputerName;
      Boolean MigrateRegistrationInfo;
      Boolean MigrateTimeZone;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_CaptureWindowsSettingsAction` class does not define any methods.

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

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`MigrateComputerName` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null, VariableName\("OSDMigrateComputerName"\)\]

`true` \(default\) to migrate the computer name.

The task sequence variable associated with this property is OSDMigrateComputerName. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

`MigrateRegistrationInfo` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null, VariableName\("OSDMigrateRegistrationInfo"\)\]

`true` \(default\) to migrate information about the registered owner or organization.

The task sequence variable associated with this property is OSDMigrateRegistrationInfo. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

`MigrateTimeZone` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null, VariableName\("OSDMigrateTimeZone"\)\]

`true` \(default\) to migrate information about the time zone.

The task sequence variable associated with this property is OSDMigrateTimeZone. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

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

\[CommandLine\("osdwinsettings.exe /capture /name:%%OSDMigrateComputerName%% /reginfo:%%OSDMigrateRegistrationInfo%% /timezone:%%OSDMigrateTimeZone%%"\),

ActionCategory{"Settings,2,7"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "CaptureWindowsSettingsControl", "TaskSequenceOptionControl"}\]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class)
