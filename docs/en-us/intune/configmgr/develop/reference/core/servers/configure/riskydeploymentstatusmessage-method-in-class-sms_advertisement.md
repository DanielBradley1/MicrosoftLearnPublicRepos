<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/riskydeploymentstatusmessage-method-in-class-sms_advertisement -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RiskyDeploymentStatusMessage Method in Class SMS\_Advertisement

The `RiskyDeploymentStatusMessage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sends a warning status message about a user deployment to a risky collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RiskyDeploymentStatusMessage (
    String DeploymentID,
    String DeploymentName,
    String PackageID,
    String CollectionID
);
```

#### Parameters

`DeploymentID` Data type: `String`

Qualifiers: \[in\]

Deployment ID.

`DeploymentName` Data type: `String`

Qualifiers: \[in\]

Name of the deployment.

`PackageID` Data type: `String`

Qualifiers: \[in\]

Package ID of the deployment.

`CollectionID` Data type: `String`

Qualifiers: \[in\]

Collection ID of the deployment.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class)
