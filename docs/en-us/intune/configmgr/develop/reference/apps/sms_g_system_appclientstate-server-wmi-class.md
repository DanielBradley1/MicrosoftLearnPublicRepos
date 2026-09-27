<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_system_appclientstate-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_System\_AppClientState Server WMI Class

The `SMS_G_System_AppClientState` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents application state.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_AppClientState : SMS_G_System
{
    UInt32 AppCI;
    UInt32 AppModelID;
    String AppModelName;
    String AppName;
    UInt32 ComplianceState;
    String MachineName;
    UInt32 ResourceID;
    UInt32 Revision;
    String UserName;
};
```

## Methods

The `SMS_G_System_AppClientState` class does not define any methods.

## Properties

`AppCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`AppModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Identifier of the application model.

`AppModelName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Name of the Application Model.

`AppName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`ComplianceState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Resource ID.

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_AppDeploymentAssetDetails Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class).

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
