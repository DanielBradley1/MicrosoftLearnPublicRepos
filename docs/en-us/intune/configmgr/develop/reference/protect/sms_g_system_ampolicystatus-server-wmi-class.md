<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_g_system_ampolicystatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_SYSTEM\_AmPolicyStatus Server WMI Class

The `SMS_G_SYSTEM_AmPolicyStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_SYSTEM_AmPolicyStatus : SMS_G_System
{
    String AssignmentUniqueID;
    String CollectionName;
    String Error;
    UInt32 ErrorCode;
    UInt32 ID;
    DateTime LastUpdateTime;
    String Name;
    UInt32 PolicyType;
    UInt32 Priority;
    UInt32 ResourceID;
    UInt32 State;
    String UniqueID;
};
```

## Methods

The `SMS_G_SYSTEM_AmPolicyStatus` class does not define any methods.

## Properties

`AssignmentUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Unique identifier for customized policy. For default policy, the value is always 'AntimalwareEx Agent'.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection. NULL for default policy as it's not targeted to any collection \(but the whole site\).

`Error` Data type: `String`

Access type: Read/Write

Qualifiers: none

The description of error when applying the policy on this computer.

`ErrorCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The error code when applying the policy on this computer.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy identifier. 0 for the default policy.

`LastUpdateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last message update time.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Policy name.

`PolicyType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy type. Possible values are:

| Value | Policy type |
| --- | --- |
| 1 | Default AM Policy |
| 2 | Customized AM Policy |

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy priority. 10000 for the default policy as it's always the lowest priority.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Client resource identifier.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The state of this policy on this computer.

| Value | Policy state |
| --- | --- |
| 1 | Success |
| 2 | Failure |

`UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for the policy.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
