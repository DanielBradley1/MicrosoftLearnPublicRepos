<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applicationinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_ApplicationInfo Server WMI Class

The `SMS_TaskSequence_ApplicationInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents application information for the application that is installed by using a task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ApplicationInfo :
{
    String Description;
    String DisplayName;
    String Name;
};
```

## Methods

The `SMS_TaskSequence_ApplicationInfo` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for Configuration Manager application.

`DisplayName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Display name for Configuration Manager application.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name for Configuration Manager application.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
