<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DCMDeploymentCompliantStatus Server WMI Class

The `SMS_DCMDeploymentCompliantStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the compliant status of a deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentCompliantStatus : SMS_BaseClass
{
    UInt32 Assets;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 BL_ID;
    String BLName;
    UInt32 BLRevision;
    UInt32 CI_ID;
    String CIName;
    DateTime DeploymentTime;
    UInt32 Revision;
    UInt32 StatusType;
    DateTime SummarizationTime;
    UInt32 SummaryType;
    String TargetCollectionID;
};
```

## Methods

The `SMS_DCMDeploymentCompliantStatus` class does not define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Number of assets related to the status.

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

The ID of the configuration item assignment. This ID is unique only for the site.

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BLName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BLRevision` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`CIName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`DeploymentTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

The time of the deployment.

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Status of the deployment from the targeted asset. Possible values are:

| Value | Deployment status |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 4 | Unknown |

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Time of the summarization.

`SummaryType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Type of the summary.

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
