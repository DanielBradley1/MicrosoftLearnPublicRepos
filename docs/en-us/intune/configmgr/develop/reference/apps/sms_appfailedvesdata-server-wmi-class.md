<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appfailedvesdata-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AppFailedVEsData Server WMI Class

The `SMS_AppFailedVEsData` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AppFailedVEsData : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    UInt32 ComplianceState;
    UInt32 DTCI;
    UInt64 DTResultID;
    UInt32 EnforcementState;
    UInt32 ErrorValue;
    String MachineName;
    String UserName;
    String VEDisplayName;
};
```

## Methods

The `SMS_AppFailedVEsData` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

AssignmentID

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

AssignmentUniqueID

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

CollectionID

`ComplianceState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

ComplianceState

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

DTCI

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[not\_null, read\]

DTResultID

`EnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

EnforcementState

`ErrorValue` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

ErrorValue

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

MachineName

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

UserName

`VEDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

VEDisplayName

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
