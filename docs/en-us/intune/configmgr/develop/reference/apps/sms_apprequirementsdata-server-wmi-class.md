<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_apprequirementsdata-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AppRequirementsData Server WMI Class

The `SMS_AppRequirementsData` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the requirements data of an application.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AppRequirementsData : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    UInt32 DTCI;
    UInt64 DTResultID;
    UInt32 InstanceGroup;
    String MachineName;
    String RequirementName;
    UInt32 RuleID;
    String SettingName;
    String SettingValue;
    String UniqueRequirementName;
    String UserName;
};
```

## Methods

The `SMS_AppRequirementsData` class does not define any methods.

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

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`InstanceGroup` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Instance group.

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`RequirementName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Name of the requirement.

`RuleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Identifier of the rule.

`SettingName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Name of the setting.

`SettingValue` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Setting value.

`UniqueRequirementName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Unique requirement name.

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
