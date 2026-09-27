<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_connectnetworkfolderaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_ConnectNetworkFolderAction Server WMI Class

The `SMS_TaskSequence_ConnectNetworkFolderAction` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that makes a connection to a network share.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConnectNetworkFolderAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      String DriveLetter;
      Boolean Enabled;
      String Name;
      String Password;
      String Path;
      String SupportedEnvironment;
      UInt32 Timeout;
      String Username;
};
```

## Methods

The `SMS_TaskSequence_ConnectNetworkFolderAction` class does not define any methods.

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

`DriveLetter` Data type: `String`

Access type: Read/Write

Qualifiers: None

Drive letter to use for connection to the network share.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("1-100"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Password` Data type: `String`

Access type: Read/Write

Qualifiers: \[VariableName\("SMSConnectNetworkFolderPassword"\), Not\_Null, Secret\]

Password to use to connect to the network share.

The task sequence variable associated with this property is SMSConnectNetworkFolderPassword. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

`Path` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

The path to which to connect.

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Username` Data type: `String`

Access type: Read/Write

Qualifiers: \[VariableName\("SMSConnectNetworkFolderAccount"\), Not\_Null\]

Account that should be used to connect to the network share.

The task sequence variable associated with this property is SMSConnectNetworkFolderAccount. For more information, see [OS deployment task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables).

## Remarks

Class qualifiers for this class include:

\[CommandLine\("smsnetuse.exe %SMSConnectNetworkFolderPath%"\),

VariablePrefix\("SMSConnectNetworkFolder"\),

ActionCategory{"General,5,1"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ConnectNetworkFolderControl", "TaskSequenceOptionControl"}\]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class)
