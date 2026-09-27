<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/getdeployments-method-in-class-sms_deployment_info -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetDeployments Method in Class SMS\_Deployment\_Info

The `GetDeployments` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets advertisement identifier or Assignment identifier and related type for a deployment that is deployed to the specified resource.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 GetDeployments(
     uint32 ResourceID,
     string DeploymentIDs[],
     uint32 DeploymentTypeID[]
);
```

#### Parameters

`ResourceID` Data type: `UInt32`

Qualifiers: \[in\]

Configuration Manager supplied ID for the resource. This ID is not unique across sites.

`DeploymentIDs` Data type: `String` Array

Qualifiers: \[out\]

Unique auto-generated key for the deployment.

`DeploymentTypeID` Data type: `UInt32` Array

Qualifiers: \[out\]

Type identifier of the deployment.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class)
