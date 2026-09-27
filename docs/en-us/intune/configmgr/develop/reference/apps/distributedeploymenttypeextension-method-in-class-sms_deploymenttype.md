<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/distributedeploymenttypeextension-method-in-class-sms_deploymenttype -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DistributeDeploymentTypeExtension Method in Class SMS\_DeploymentType

The `DistributeDeploymentTypeExtension` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, schedules a Deployment Type Extension to be distributed throughout the hierarchy.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 DistributeDeploymentTypeExtension (
     string TechnologyExtensionFileName
);
```

#### Parameters

`TechnologyExtensionFileName` Data type: `String`

Qualifiers: \[in\]

Filename of the technology extension.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_DeploymentType Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymenttype-server-wmi-class)
