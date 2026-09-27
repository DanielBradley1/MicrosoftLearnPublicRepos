<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentrequirementsnotmetassetdetails-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AppDeploymentRequirementsNotMetAssetDetails Server WMI Class

The `SMS_AppDeploymentRequirementsNotMetAssetDetails` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents asset-level details of application deployments where requirements are not met.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDeploymentRequirementsNotMetAssetDetails : SMS_BaseClass
{
    UInt32 AppCI;
    String AppName;
    UInt32 AppStatusType;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    String CollectionName;
    String CurrentReqValue;
    UInt32 DeploymentIntent;
    UInt32 DTCI;
    UInt32 DTModelID;
    String DTName;
    UInt32 DTPresent;
    UInt64 DTResultID;
    UInt32 EnforcementState;
    UInt32 ExtendedInfoDescriptionID;
    UInt32 ExtendedInfoID;
    Boolean IsMachineAssignedToUser;
    Boolean IsMachineChangesPersisted;
    Boolean IsVM;
    UInt32 MachineID;
    String MachineName;
    String MachineOS;
    UInt32 PolicyModelID;
    String RequirementName;
    UInt32 RequirementType;
    UInt32 Revision;
    UInt32 RuleID;
    DateTime StartTime;
    UInt32 StatusType;
    String Technology;
    String UniqueRequirementName;
    UInt32 UpdateState;
    String UserName;
    String VMHostName;
};
```

## Methods

The `SMS_AppDeploymentRequirementsNotMetAssetDetails` class does not define any methods.

## Properties

`AppCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AppName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AppStatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`CurrentReqValue` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Current requirement value.

`DeploymentIntent` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTPresent` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Deployment type present.

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Deployment type result identifier.

`EnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

Enforcement state. Possible values are:

| Value | Enforcement state |
| --- | --- |
| 0 | Enforcement state unknown |
| 1 | Enforcement started |
| 2 | Enforcement waiting for content |
| 3 | Waiting for another installation to complete |
| 4 | Waiting for maintenance window before installing |
| 5 | Restart required before installing |
| 6 | General failure |
| 7 | Pending installation |
| 8 | Installing update |
| 9 | Pending system restart |
| 10 | Successfully installed update |
| 11 | Failed to install update |
| 12 | Downloading update |
| 13 | Downloaded update |
| 14 | Failed to download update |

`ExtendedInfoDescriptionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`ExtendedInfoID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`IsMachineAssignedToUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`IsMachineChangesPersisted` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`IsVM` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`MachineID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`MachineOS` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Computer operating system.

`PolicyModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`RequirementName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Name of requirement.

`RequirementType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Type of requirement that has not been met. Possible values are:

| Value | Type of requirement violation |
| --- | --- |
| 0 | Constraint violation |
| 1 | Conflict violation |
| 2 | Enforcement violation |
| 3 | Requirement violation |
| 4 | Dependency violation |

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`RuleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Rule ID of the requirement that has not been met.

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`Technology` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`UniqueRequirementName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Name of unique requirement.

`UpdateState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`VMHostName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
