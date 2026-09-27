<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrorstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DCMDeploymentErrorStatus Server WMI Class

The `SMS_DCMDeploymentErrorStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents error status for a deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentErrorStatus : SMS_BaseClass
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
    UInt32 ErrorCode;
    String ErrorDescription;
    UInt32 ErrorType;
    String ErrorTypeDisplay;
    String ObjectDescription;
    UInt32 ObjectID;
    String ObjectName;
    UInt32 ObjectType;
    String ObjectTypeName;
    UInt32 Revision;
    String RuleStateDisplay;
    UInt32 StatusType;
    DateTime SummarizationTime;
    UInt32 SummaryType;
    String TargetCollectionID;
};
```

## Methods

The `SMS_DCMDeploymentErrorStatus` class does not define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Count of assets related to the status.

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

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

Time of the deployment.

`ErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Error code.

`ErrorDescription` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Description of the error.

`ErrorType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, key, not\_null, read\]

Type of error. Possible value are:

| Value | Error type |
| --- | --- |
| 1 | INFRASTRUCTURAL |
| 2 | DISCOVERY |
| 3 | CONFLICT |
| 4 | ENFORCEMENT |

`ErrorTypeDisplay` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

The description of the error type.

`ObjectDescription` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Description of the object.

`ObjectID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

ID of the object.

`ObjectName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Name of the object.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, key, not\_null, read\]

Object type. Possible values are:

| Value | Object type |
| --- | --- |
| 1 | CI |
| 2 | SETTING |
| 3 | RULE |

`ObjectTypeName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Name of the object type.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, key, not\_null, read\]

Object type. Possible values are:

| Value | Object type |
| --- | --- |
| 1 | CI |
| 2 | SETTING |
| 3 | RULE |

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleStateDisplay` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Time of summarization.

`SummaryType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Type of summary.

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
