<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_requeststatestoreaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_RequestStateStoreAction Server WMI Class

The `SMS_TaskSequence_RequestStateStoreAction` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that requests access to a state migration point when capturing a state from a computer or restoring a state to a computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_RequestStateStoreAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      Boolean FallbackToNAA;
      String Name;
      String RequestType;
      UInt32 SMPRetryCount;
      UInt32 SMPRetryTime;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_RequestStateStoreAction` class does not define any methods.

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

`FallbackToNAA` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the action should use the network access account \(NAA\) as a fallback when the computer account fails to connect to the state migration point. The default value is `false`.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("1-100"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`RequestType` Data type: `String`

Access type: Read/Write

Qualifiers: \[CommandLineArg\(1\), Not\_Null\]

Type of state migration point \(SMP\) request. Possible values are:

- capture
- restore

  `SMPRetryCount` Data type: `UInt32`

  Access type: Read/Write

  Qualifiers: \[Global, ValueRange\("0-30"\)\]

  The number of times that the action should try to find a state migration point before failing \(global setting\). The value must be between 0 and 30.

  `SMPRetryTime` Data type: `UInt32`

  Access type: Read/Write

  Qualifiers: \[Global, ValueRange\("0-600"\)\]

  The time, in seconds, that the action should wait between retry attempts \(global setting\).The value must be between 0 and 600.

  `SupportedEnvironment` Data type: `String`

  Access type: Read/Write

  Qualifiers: \[Not\_Null:ToInstance\]

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

  The default value of this property for this task sequence action is FullOS.

  `Timeout` Data type: `UInt32`

  Access type: Read/Write

  Qualifiers: None

  See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

\[CommandLine\("osdsmpclient.exe /%1"\),VariablePrefix\("OSDState"\),

ActionCategory\("UserState,1,4"\),ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "RequestStateStoreControl", "TaskSequenceOptionControl"}\]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
