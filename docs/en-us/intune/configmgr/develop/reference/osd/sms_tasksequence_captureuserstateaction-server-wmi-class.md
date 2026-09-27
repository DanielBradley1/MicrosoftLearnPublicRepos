<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_captureuserstateaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_CaptureUserStateAction Server WMI Class

The `SMS_TaskSequence_CaptureUserStateAction` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that uses the User State Migration Tool \(USMT\) to capture user state and settings from the target computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_CaptureUserStateAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      String ConfigFiles[];
      Boolean ContinueOnError;
      Boolean ContinueOnLockedFiles;
      String Description;
      Boolean Enabled;
      Boolean EnableVerboseLogging;
      String FileAccess;
      String Mode;
      String Name;
      Boolean OfflineUserState;
      Boolean SkipEncryptedFiles;
      String SupportedEnvironment;
      UInt32 Timeout;
      Boolean UseHardlinks;
      String UsmtPackageID;
};
```

## Methods

The `SMS_TaskSequence_CaptureUserStateAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`ConfigFiles` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

The configuration files used to capture user profiles. Set this property for customized user profile migration.

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`ContinueOnLockedFiles` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[Not\_Null, VariableName\("OSDMigrateContinueOnLockedFiles"\)\]

`true` \(default\) to allow the capture user state action to proceed even if some files cannot be captured. This property is required.

The task sequence variable associated with this property is OSDMigrateContinueOnLockedFiles. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("0-255"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`EnableVerboseLogging` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

`true` to enable verbose logging for the USMT. The default value is `false`. This property is required.

`FileAccess` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

Corresponds to the UI option to **Copy by using file system access**.

- Normal \(default\)
- VSS

  `Mode` Data type: `String`

  Access type: Read/Write

  Qualifiers: \[Not\_Null\]

  Mode that allows customization of the files captured by the USMT. Possible values are:
- Simple \(default\)
- Advanced

  This property is required.

  `Name` Data type: `String`

  Access type: Read/Write

  Qualifiers: \[AllowedLen\("1-100"\)\]

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

  `OfflineUserState` Data type: `Boolean`

  Access type: Read/Write

  Qualifiers: \[Not\_Null, VariableName\("\_OSDMigrateOfflineUserState"\)\]

  `true` to migrate offline user state. The default value is `false`.

  `SkipEncryptedFiles` Data type: `Boolean`

  Access type: Read/Write

  Qualifiers: \[Not\_Null, VariableName\("OSDMigrateSkipEncryptedFiles"\)\]

  `true` to skip encrypted files. The default value is `false`.

  The task sequence variable associated with this property is OSDMigrateSkipEncryptedFiles. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

  `SupportedEnvironment` Data type: `String`

  Access type: Read/Write

  Qualifiers: \[Not\_Null:ToInstance\]

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

  The default value of this property for this task sequence action is FullOS.

  `Timeout` Data type: `UInt32`

  Access type: Read/Write

  Qualifiers: None

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

  `UseHardlinks` Data type: `Boolean`

  Access type: Read/Write

  Qualifiers: \[Not\_Null, VariableName\("\_OSDMigrateUseHardlinks"\)\]

  `true` to configure USMT to use hardlinks. The default value is `false`.

  `UsmtPackageID` Data type: `String`

  Access type: Read/Write

  Qualifiers: \[Not\_Null, VariableName\("\_OSDMigrateUsmtPackageID"\), TaskSequencePackage\]

  The ID of the Configuration Manager package that contains USMT binaries. This property is required.

  The task sequence variable associated with this property is \_OSDMigrateUsmtPackageID. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

## Remarks

Class qualifiers for this class include:

\[CommandLine\("osdmigrateuserstate.exe /collect /continueOnError:%%OSDMigrateContinueOnLockedFiles%% /skipefs:%%OSDMigrateSkipEncryptedFiles%%"\),VariablePrefix\("OSDMigrate"\),

ActionCategory{"UserState,2,4"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "CaptureUserStateControl", "TaskSequenceOptionControl"}\]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class)
