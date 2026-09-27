<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdtdeploymentsummary-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AppDTDeploymentSummary Server WMI Class

The `SMS_AppDTDeploymentSummary` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the deployment type-level summary of application deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDTDeploymentSummary : SMS_BaseClass
{
    UInt32 AppCI;
    String AppModelName;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    String CollectionName;
    UInt32 DeploymentIntent;
    DateTime DeploymentTime;
    String Description;
    UInt32 DTCI;
    String DTModelName;
    DateTime ModificationTime;
    SInt32 NumberAlreadyPresent;
    SInt32 NumberErrors;
    SInt32 NumberInProgress;
    SInt32 NumberInstalled;
    SInt32 NumberReqsNotMet;
    DateTime SummarizationTime;
    String Technology;
};
```

## Methods

The `SMS_AppDTDeploymentSummary` class does not define any methods.

## Properties

`AppCI` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AppModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model Name of the application.

`AssignmentID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).The ID of the collection to which the deployment was deployed.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DeploymentIntent` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DeploymentTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time the deployment was created.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the deployment type.

`DTCI` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model name of the deployment type.

`ModificationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time that the deployment type was last modified.

`NumberAlreadyPresent` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that have this deployment type installed.

`NumberErrors` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that return an error during an installation.

`NumberInProgress` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that have this deployment type installation in progress.

`NumberInstalled` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that have this deployment type installed.

`NumberReqsNotMet` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that do not meet the requirements of this deployment type.

`SummarizationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time when summarization occurs.

`Technology` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
