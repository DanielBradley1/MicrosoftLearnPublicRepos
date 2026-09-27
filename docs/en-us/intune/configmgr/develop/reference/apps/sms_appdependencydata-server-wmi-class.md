<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdependencydata-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AppDependencyData Server WMI Class

The `SMS_AppDependencyData` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents application deployment dependency data.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDependencyData : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    UInt32 ComplianceState;
    String DependencyGroup;
    String DependentDTName;
    UInt32 DTCI;
    UInt32 DTModelID;
    UInt64 DTResultID;
    UInt32 EnforcementState;
    UInt32 ErrorValue;
    String MachineName;
    String UserName;
};
```

## Methods

The `SMS_AppDependencyData` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class)..

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`ComplianceState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DependencyGroup` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Name of the Dependency group.

`DependentDTName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Name of the dependent deployment type.

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`EnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

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

`ErrorValue` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Last return value.

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

Name of the computer that created the message.

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
