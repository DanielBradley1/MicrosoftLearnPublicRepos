<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_installapplicationaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_InstallApplicationAction server WMI class

The `SMS_TaskSequence_InstallApplicationAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that installs an application.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_InstallApplicationAction : SMS_TaskSequence_Action
{
    SMS_TaskSequence_ApplicationInfo AppInfo[];
    String ApplicationName;
    String BaseVariableName;
    boolean ClearCache;
    SMS_TaskSequence_Condition Condition;
    Boolean ContinueOnError;
    Boolean ContinueOnInstallError;
    String Description;
    Boolean Enabled;
    String Name;
    UInt32 NumApps;
    String RetryCount;
    String SupportedEnvironment;
    UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_InstallApplicationAction` class doesn't define any methods.

## Properties

### `AppInfo`

Data type: `SMS_TaskSequence_ApplicationInfo` Array

Access type: Read/Write

Qualifiers: `[variablename]`

An array of [SMS\_TaskSequence\_ApplicationInfo server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applicationinfo-server-wmi-class) class objects. Each element contains application details, such as display name, model name of the application, and description.

### `ApplicationName`

Data type: `String`

Access type: Read/Write

Qualifiers: `[commandlinearg, tasksequenceapplication]`

Comma-separated list of application model names for the step to install.

### `BaseVariableName`

Data type: `String`

Access type: Read/Write

Qualifiers: `[commandlinearg, requiredifnull]`

This variable specifies the base name for a set of task sequence variables specified for a collection or a computer. These variables specify the applications that the step installs for that collection or computer. Each variable name consists of its common base name plus a numerical suffix starting at `01`. The value for each variable must contain the name of the application and nothing else.

### `ClearCache`

Data type: `Boolean`

Access type: Read/write

Set to `true` to clear application content from the cache after installing. This value is `false` by default.

### `Condition`

Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `ContinueOnError`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `ContinueOnInstallError`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[commandlinearg, requiredifnotnull]`

Set `true` to continue if there's an installation error. This property is required.

### `Description`

Data type: `String`

Access type: Read/Write

Qualifiers: `[allowedlen]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[allowedlen]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `NumApps`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: `[variablename]`

Size of the array indicated by the `AppInfo` property. The task sequence variable associated with this property is `OSDAppCount`.

### `RetryCount`

Data type: `String`

Access type: Read/Write

Qualifiers: `[retrycount]`

The number of retries. The default value is `2`.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[not_null, valuemap]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

```
[CommandLine("smsappinstall.exe /app:%1 /basevar:%2 /continueOnError:%3"),

ActionCategory{"Software,1,2"},     ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "InstallApplicationControl", "TaskSequenceOptionControl"}]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime requirements

For more information, see [Configuration Manager server runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development requirements

For more information, see [Configuration Manager server development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
