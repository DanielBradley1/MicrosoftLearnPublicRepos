<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_system_dcmdeploymentcompliantassetdetails-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_SYSTEM\_DCMDeploymentCompliantAssetDetails Server WMI Class

The `SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents compliant asset details for a deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails : SMS_G_System
{
    UInt32 AssignmentID;
    UInt32 BL_ID;
    UInt32 CI_ID;
    UInt32 ResourceID;
    UInt32 Rule_ID;
};
```

## Methods

The `SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

ID of the configuration item assignment. This ID is unique only for the site.

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Baseline ID.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Unique ID of the configuration item. This ID is unique only for the site.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Unique ID, supplied by Configuration Manager, that identifies a client resource. This ID is not unique across sites.

`Rule_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Description of the rule ID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
