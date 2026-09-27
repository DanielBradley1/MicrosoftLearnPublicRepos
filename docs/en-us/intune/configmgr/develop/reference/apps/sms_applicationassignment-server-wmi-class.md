<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_applicationassignment-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ApplicationAssignment Server WMI Class

The `SMS_ApplicationAssignment` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the assignment of an application to a collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ApplicationAssignment : SMS_CIAssignmentBaseClass
{
    String ApplicationName;
    Boolean ApplyToSubTargets;
    UInt32 AppModelID;
    String AssignedCI_UniqueID;
    SInt32 AssignedCIs[];
    SInt32 AssignmentAction;
    String AssignmentDescription;
    SInt32 AssignmentID;
    String AssignmentName;
    SInt32 AssignmentType;
    String AssignmentUniqueID;
    String CollectionName;
    Boolean ContainsExpiredUpdates;
    DateTime CreationTime;
    SInt32 DesiredConfigType;
    Boolean DisableMomAlerts;
    UInt32 DPLocality;
    Boolean Enabled;
    DateTime EnforcementDeadline;
    String EvaluationSchedule;
    DateTime ExpirationTime;
    DateTime LastModificationTime;
    String LastModifiedBy;
    UInt32 LocaleID;
    Boolean LogComplianceToWinEvent;
    SInt32 NonComplianceCriticality;
    Boolean NotifyUser;
    UInt32 OfferFlags;
    SInt32 OfferTypeID;
    Boolean OverrideServiceWindows;
    SMS_ApplicationPolicyTemplateBinding PolicyBinding[];
    SInt32 Priority;
    Boolean RaiseMomAlertsOnFailure;
    Boolean RebootOutsideOfServiceWindows;
    Boolean RequireApproval;
    Boolean SendDetailedNonComplianceStatus;
    String SourceSite;
    DateTime StartTime;
    UInt32 StateMessagePriority;
    UInt32 SuppressReboot;
    String TargetCollectionID;
    DateTime UpdateDeadline;
    Boolean UpdateSupersedence;
    Boolean UseGMTTimes;
    Boolean UserUIExperience;
    Boolean WoLEnabled;
};
```

## Methods

The `SMS_ApplicationAssignment` class does not define any methods.

## Properties

`ApplicationName` Data type: `String`

Access type: Read-only

Qualifiers: \[readonly\]

Name of the application.

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[deprecated\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AppModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[readonly\]

AppModelID description.

`AssignedCI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignedCIs` Data type: `SInt32 Array`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentAction` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[enumeration, not\_null, enumeration, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key, key\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentName` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: \[readonly\]

Name of the collection to which the deployment was deployed.

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DesiredConfigType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[enumeration, not\_null, enumeration, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DisableMomAlerts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DPLocality` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`ExpirationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LogComplianceToWinEvent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`NonComplianceCriticality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`OfferFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits, not\_null\]

Offer flags. Possible values are:

| Value | Offer flag |
| --- | --- |
| 1 | PREDEPLOY |
| 2 | ONDEMAND |
| 4 | ENABLEPROCESSTERMINATION |
| 8 | ALLOWUSERSTOREPAIRAPP |
| 16 | RELATIVESCHEDULE |
| 32 | HIGHIMPACTDEPLOYMENT |

`OfferTypeID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[enumeration, not\_null\]

Type of offer. Possible values are:

| Value | Offer type |
| --- | --- |
| 0 | REQUIRED |
| 2 | AVAILABLE |

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`PolicyBinding` Data type: `SMS_ApplicationPolicyTemplateBinding Array`

Access type: Read/Write

Qualifiers: none

The dynamic binding of an application policy to a deployment type.

`Priority` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[enumeration, not\_null\]

Priority for installation of the application. Possible values are:

| Value | Installation priority |
| --- | --- |
| 0 | LOW |
| 1 | MEDIUM |
| 2 | HIGH |

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RequireApproval` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

`true` if the request for this user-available assignment requires approval from the administrator.

`SendDetailedNonComplianceStatus` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`StateMessagePriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[valuemap, values\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`SuppressReboot` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UpdateDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Deadline for updates.

`UpdateSupersedence` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

`true` if you should update the supersedence; otherwise, `false`.

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UserUIExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

`true` if user notification is displayed; otherwise, `false`.

`WoLEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
