<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_resourceclientsettingsassignment-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_SYSTEM\_ResourceClientSettingsAssignment Server WMI Class

The `SMS_G_System_ResourceClientSettingsAssignment` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents resource-specific \(device or user\) client agent settings assignments.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_ResourceClientSettingsAssignment : SMS_G_System
{
     String AssignmentUniqueID;
     String CollectionName;
     UInt32 ID;
     String Name;
     UInt32 Priority;
     String UniqueID;
     UInt32 ResourceID;
     UInt32 Type;
};
```

## Methods

The `SMS_G_System_ResourceClientSettingsAssignment` class does not define any methods.

## Properties

`AssignmentUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Assignment Unique ID.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the collection.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Identifier.

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Identifier.

`UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: None

Unique identifier for the settings.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class).

`Type` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Settings type. Possible values are:

| Value | Settings type |
| --- | --- |
| 1 | Device |
| 2 | User |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
