<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationpolicyassignment-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ConfigurationPolicyAssignment Server WMI Class

The `SMS_ConfigurationPolicyAssignment` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the deployment of an instance of `SMS_ConfigurationPolicy`. It is similar to `SMS_BaselineAssignment`, except that `SMS_ConfigurationPolicy` is deployed directly, instead of being collected into a baseline first.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationPolicyAssignment : SMS_CIAssignmentBaseClass
{
    Boolean ApplyToSubTargets;
    String AssignedCI_UniqueID;
    SInt32 AssignedCIs[];
    SInt32 AssignmentAction;
    String AssignmentDescription;
    SInt32 AssignmentID;
    String AssignmentName;
    SInt32 AssignmentType;
    String AssignmentUniqueID;
    Boolean ContainsExpiredUpdates;
    DateTime CreationTime;
    SInt32 DesiredConfigType;
    Boolean DisableMomAlerts;
    UInt32 DPLocality;
    Boolean Enabled;
    DateTime EnforcementDeadline;
    Boolean EnforcementEnabled;
    String EvaluationSchedule;
    DateTime ExpirationTime;
    DateTime LastModificationTime;
    String LastModifiedBy;
    Boolean LimitStateMessageVerbosity;
    UInt32 LocaleID;
    Boolean LogComplianceToWinEvent;
    SInt32 NonComplianceCriticality;
    Boolean NotifyUser;
    Boolean OverrideServiceWindows;
    Boolean PersistOnWriteFilterDevices;
    Boolean RaiseMomAlertsOnFailure;
    UInt32 RandomizationMinutes;
    Boolean RebootOutsideOfServiceWindows;
    Boolean SendDetailedNonComplianceStatus;
    String SourceSite;
    DateTime StartTime;
    UInt32 StateMessagePriority;
    UInt32 StateMessageVerbosity;
    UInt32 SuppressReboot;
    String TargetCollectionID;
    Boolean UseGMTTimes;
    Boolean UserUIExperience;
    Boolean WoLEnabled;
};
```

## Methods

The `SMS_ConfigurationPolicyAssignment` class does not define any methods.

## Properties

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[deprecated\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`AssignedCI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Unique identifier of the assigned baseline configuration item.

`AssignedCIs` Data type: `SInt32 Array`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentAction` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[enumeration, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key, key\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentName` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`DesiredConfigType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[enumeration, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`DisableMomAlerts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`DPLocality` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`EnforcementEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_BaselineAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class).

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`ExpirationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`LastModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`LimitStateMessageVerbosity` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null, obsoleted\]

This method/property has been removed or deprecated in Configuration Manager SP1.

`LocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`LogComplianceToWinEvent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`NonComplianceCriticality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`PersistOnWriteFilterDevices` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`RandomizationMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Random time in minutes that is used when evaluating an assignment automatically once it arrives at the client. The random evaluation interval distributes the processing load when multiple assignments arrive at the client at same time.

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`SendDetailedNonComplianceStatus` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`StateMessagePriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[valuemap, values\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`StateMessageVerbosity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

See [SMS\_UpdateGroupAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updategroupassignment-server-wmi-class).

`SuppressReboot` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits, not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

`UserUIExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

`true` if user notification is displayed; otherwise, `false`.

`WoLEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS\_CIAssignmentBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
