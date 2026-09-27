<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/updatedeployment-method-in-class-sms_deploymentsummary -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateDeployment Method in Class SMS\_DeploymentSummary

The `UpdateDeployment` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates the summarized results for a specific Classic Deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 UpdateDeployment (
     uint32 AssignmentID
);
```

#### Parameters

`AssignmentID` Data type: `UInt32`

Qualifiers: \[in\]

Identifier of the configuration item assignment. This identifier is unique only for the site.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_DeploymentSummary Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymentsummary-server-wmi-class)
