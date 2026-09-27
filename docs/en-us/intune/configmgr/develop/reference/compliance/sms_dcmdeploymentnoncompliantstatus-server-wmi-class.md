<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentnoncompliantstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DCMDeploymentNonCompliantStatus Server WMI Class

The `SMS_DCMDeploymentNonCompliantStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents non-compliant status for a deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentNonCompliantStatus : SMS_BaseClass
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
    Boolean IsBaselineRule;
    UInt32 Revision;
    UInt32 Rule_ID;
    String RuleDescription;
    String RuleName;
    UInt32 RuleSeverity;
    String RuleStateDisplay;
    UInt32 RuleSubState;
    UInt32 StatusType;
    DateTime SummarizationTime;
    UInt32 SummaryType;
    String TargetCollectionID;
    String ValidationRule;
};
```

## Methods

The `SMS_DCMDeploymentNonCompliantStatus` class does not define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Number of assets related to the status.

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

Deployment time.

`IsBaselineRule` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`Rule_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleDescription` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleSeverity` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Severity of the rule.

`RuleStateDisplay` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleSubState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Rule sub-status type. .

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Summarization time.

`SummaryType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Summary type.

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`ValidationRule` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
