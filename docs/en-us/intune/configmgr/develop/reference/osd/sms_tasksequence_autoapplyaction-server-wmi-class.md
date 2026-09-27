<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_autoapplyaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_AutoApplyAction Server WMI Class

The `SMS_TaskSequence_AutoApplyAction` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that matches and installs device drivers as part of an operating system deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_AutoApplyAction : SMS_TaskSequence_Action
{
      Boolean BestMatch;
      String CategoryList[];
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
      Boolean UnsignedDriver;
};
```

## Methods

The `SMS_TaskSequence_AutoApplyAction` class does not define any methods.

## Properties

`BestMatch` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

`true` \(default\) to install the device driver that is the best match for the hardware device. Set this property to `false` to install all compatible device drivers and have the operating system choose the best driver to use.

Note

This property is required by the task sequence action if there are multiple device drivers in the driver catalog that are compatible with the hardware device.

`CategoryList` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Unique IDs of categories for which the task sequence action searches in the driver catalog. The default value is `null`.

You can obtain the available category IDs by enumerating the SMS\_CategoryInstance Server WMI Class objects on the site.

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

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("1-100"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is WinPE.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`UnsignedDriver` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[Not\_Null, VariableName\("OSDAllowUnsignedDriver"\)\]

`true` to configure the Windows operating system to allow unsigned device drivers to be installed. The default value is `false`.

Note

This property is required by the action. However, it's deprecated and not used by modern OS versions.

## Remarks

Class qualifiers for this class include:

\[CommandLine\("osddriverclient.exe /auto /bestmatch:%%OSDAutoApplyDriverBestMatch%% /unsigned:%%OSDAllowUnsignedDriver%%"\),

ActionCategory{"Drivers,1,6"},VariablePrefix\("OSDAutoApplyDriver"\),

ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "AutoApplyDriverControl", "TaskSequenceOptionControl"}\]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class)
