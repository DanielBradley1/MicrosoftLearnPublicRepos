<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_cideploymentunknownstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIDeploymentUnknownStatus Server WMI Class

The `SMS_CIDeploymentUnknownStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the status of a configuration item deployment for unknown status.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CIDeploymentUnknownStatus : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 Category;
    UInt32 CI_ID;
    String CollectionID;
    String CollectionName;
    UInt32 DeploymentIntent;
    UInt32 PolicyModelID;
    String SoftwareName;
    DateTime StartTime;
    UInt32 Total;
};
```

## Methods

The `SMS_CIDeploymentUnknownStatus` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`Category` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Status category.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

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

`PolicyModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Model ID of the policy.

`SoftwareName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Name of the software.

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`Total` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Total number of resources in this state.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
