<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentnoncompliantassetdetails-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DCMDeploymentNonCompliantAssetDetails Server WMI Class

The `SMS_DCMDeploymentNonCompliantAssetDetails` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents non-compliant asset details for a deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentNonCompliantAssetDetails : SMS_BaseClass
{
    UInt32 AssetID;
    String AssetName;
    UInt32 AssetType;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 BL_ID;
    String BLName;
    UInt32 BLRevision;
    UInt32 CI_ID;
    String CIName;
    UInt32 ClientType;
    String ClientTypeDisplay;
    Boolean IsBaselineRule;
    Boolean IsEnforced;
    Boolean IsMachineAssignedToUser;
    Boolean IsMachineChangesPersisted;
    Boolean IsVM;
    UInt32 Revision;
    UInt32 Rule_ID;
    String RuleDescription;
    String RuleName;
    UInt32 RuleSeverity;
    String RuleStateDisplay;
    UInt32 RuleSubState;
    UInt32 StatusType;
    String TargetCollectionID;
    String ValidationRule;
    String VMHostName;
};
```

## Methods

The `SMS_DCMDeploymentNonCompliantAssetDetails` class doesn't define any methods.

## Properties

`AssetID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`AssetName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Name of the asset.

`AssetType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

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

`ClientType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`ClientTypeDisplay` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`IsBaselineRule` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`IsEnforced` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

`true` if this is enforced.

`IsMachineAssignedToUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`true` if the computer is assigned to a user.

`IsMachineChangesPersisted` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`true` if the virtual machine changes are persisted.

`IsVM` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`true` if this is a virtual machine. True, if this is a virtual machine.

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

Name of the rule.

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

Rule sub-state.

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`ValidationRule` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`VMHostName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Virtual machine host name.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
