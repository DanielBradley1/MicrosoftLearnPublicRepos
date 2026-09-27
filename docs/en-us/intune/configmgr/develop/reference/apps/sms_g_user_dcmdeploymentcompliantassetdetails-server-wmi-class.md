<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_user_dcmdeploymentcompliantassetdetails-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_USER\_DCMDeploymentCompliantAssetDetails Server WMI Class

The `SMS_G_USER_DCMDeploymentCompliantAssetDetails` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents compliant asset details for a deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_USER_DCMDeploymentCompliantAssetDetails : SMS_G_User
{
    UInt32 AssignmentID;
    UInt32 BL_ID;
    UInt32 CI_ID;
    UInt32 ResourceID;
    UInt32 Rule_ID;
};
```

## Methods

The `SMS_G_USER_DCMDeploymentCompliantAssetDetails` class doesn't define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentErrorAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_DCMDeploymentErrorAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Configuration item ID.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Unique ID, supplied by Configuration Manager, that identifies a client resource. This ID isn't unique across sites.

`Rule_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Rule ID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
