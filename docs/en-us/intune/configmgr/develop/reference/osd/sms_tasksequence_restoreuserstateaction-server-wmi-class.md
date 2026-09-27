<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_restoreuserstateaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_RestoreUserStateAction Server WMI Class

The `SMS_TaskSequence_RestoreUserStateAction` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that initiates the User State Migration Tool \(USMT\) to restore user state and settings to a target computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_RestoreUserStateAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      String ConfigFiles[];
      Boolean ContinueOnError;
      Boolean ContinueOnRestore;
      String Description;
      Boolean Enabled;
      Boolean EnableVerboseLogging;
      String LocalAccountPassword;
      Boolean LocalAccounts;
      String Mode;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
      String UsmtRestorePackageID;
};
```

## Methods

The `SMS_TaskSequence_RestoreUserStateAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`ConfigFiles` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Configuration files used to capture user profiles. Set this property for customized user profile migration.

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`ContinueOnRestore` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null, VariableName\("OSDMigrateContinueOnRestore"\)\]

`true` \(default\) if user state restoration should continue even if some files cannot be restored.

The task sequence variable associated with this property is OSDMigrateContinueOnRestore. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

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

`true` to enable USMT verbose logging. The default value is `false`.

`LocalAccountPassword` Data type: `String`

Access type: Read/Write

Qualifiers: \[VariableName\("OSDMigrateLocalAccountPassword"\), Secret\]

Password for the local user account to reset for restored local user profiles.

The task sequence variable associated with this property is OSDMigrateLocalAccountPassword. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

`LocalAccounts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[VariableName\("OSDMigrateLocalAccounts"\), Not\_Null\]

`true` to restore the local computer account. The default value is `false`.

The task sequence variable associated with this property is OSDMigrateLocalAccounts. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

`Mode` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

Mode for customizing the USMT file list. Possible values are shown below. The default value is Simple.

- Simple
- Advanced

  `Name` Data type: `String`

  Access type: Read/Write

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

  `SupportedEnvironment` Data type: `String`

  Access type: Read/Write

  Qualifiers: \[Not\_Null:ToInstance\]

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

  The default value of this property for this task sequence action is FullOS.

  `Timeout` Data type: `UInt32`

  Access type: Read/Write

  Qualifiers: None

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

  `UsmtRestorePackageID` Data type: `String`

  Access type: Read/Write

  Qualifiers: \[Not\_Null, TaskSequencePackage, VariableName\("\_OSDMigrateUsmtRestorePackageID"\)\]

  ID of the task sequence package containing the USMT program.

  The task sequence variable associated with this property is \_OSDMigrateUsmtRestorePackageID. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

## Remarks

Class qualifiers for this class include:

\[CommandLine\("osdmigrateuserstate.exe /apply /continueOnError:%%OSDMigrateContinueOnRestore%%"\),

VariablePrefix\("OSDMigrate"\),

ActionCategory{"UserState,3,4"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "RestoreUserStateControl", "TaskSequenceOptionControl"}\]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
