<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AppDeploymentStatus Server WMI Class

The `SMS_AppDeploymentStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents application deployment status.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDeploymentStatus : SMS_BaseClass
{
    UInt32 AppCI;
    String AppName;
    UInt32 AppStatusType;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    String CollectionName;
    UInt32 DeploymentIntent;
    UInt32 DTCI;
    UInt32 DTModelID;
    String DTName;
    UInt32 EnforcementState;
    UInt32 PolicyModelID;
    DateTime StartTime;
    UInt32 StatusType;
    String Technology;
    UInt32 Total;
};
```

## Methods

The `SMS_AppDeploymentStatus` class does not define any methods.

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

`DeploymentIntent` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`EnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

Enforcement state. Possible values are:

| Value | Enforcement state |
| --- | --- |
| 0 | Enforcement State Unknown |
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

`PolicyModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Policy Model ID of the application.

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

`Total` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Total number of systems at a specific status for the deployment.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
