<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_downloadpackagecontentaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_DownloadPackageContentAction Server WMI Class

The `SMS_TaskSequence_DownloadPackageContentAction` Windows Management Instrumentation \(WMI\) class is an SMS provider server class, in Configuration Manager, that represents a task sequence action that downloads the contents of a package.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_DownloadPackageContentAction : SMS_TaskSequence_Action
{
    SMS_TaskSequence_Condition Condition;
    Boolean ContinueDownloadOnError;
    Boolean ContinueOnError;
    String Description;
    String DestinationCustomPath;
    String DestinationLocationType;
    String DestinationVariable;
    String DownloadPackages;
    Boolean Enabled;
    String Name;
    UInt32 NumPackages;
    SMS_TaskSequence_PackageInfo PackageInfo[];
    String SupportedEnvironment;
    UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_DownloadPackageContentAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`ContinueDownloadOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to continue to the next package if a package fails to download. The default value is `true`.

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("0-255"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`DestinationCustomPath` Data type: `String`

Access type: Read/Write

Qualifiers: \[VariableName\("OSDDownloadDestinationPath"\)\]

The destination path.

`DestinationLocationType` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null, ValueMap\]

The destination location type. The default value is TSCache. Possible values are:

| Value |
| --- |
| TSCache |
| CCMCache |
| Custom |

`DestinationVariable` Data type: `String`

Access type: Read/Write

Qualifiers: none

The destination variable.

`DownloadPackages` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null, TaskSequencePackageList\]

Comma separated list of package Ids to be downloaded.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[AllowedLen\("1-100"\)\]

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`NumPackages` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[VariableName\("OSDPackageCount"\)\]

The total number of packages.

`PackageInfo` Data type: `SMS_TaskSequence_PackageInfo Array`

Access type: Read/Write

Qualifiers: \[VariableName\("OSDPackage"\)\]

An array of task sequence information package information.

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: none

The default value is WinPEandFullOS. See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
