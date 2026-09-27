<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appconflictsdata-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AppConflictsData Server WMI Class

The `SMS_AppConflictsData` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the conflict of an application deployment configuration.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AppConflictsData : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    String ConflictsWith;
    UInt32 DTCI;
    UInt64 DTResultID;
    String MachineName;
    String RequiredBy;
    String UserName;
};
```

## Methods

The `SMS_AppConflictsData` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`ConflictsWith` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Name of the conflicting deployment type.

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`RequiredBy` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Deployment type that depends on the conflicted deployment.

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
