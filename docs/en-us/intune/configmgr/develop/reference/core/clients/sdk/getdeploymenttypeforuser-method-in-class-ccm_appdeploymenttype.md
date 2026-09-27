<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getdeploymenttypeforuser-method-in-class-ccm_appdeploymenttype -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# GetDeploymentTypeForUser Method in Class CCM\_AppDeploymentType

The `GetDeploymentTypeForUser` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that retrieves the application deployment type property for a user.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetDeploymentTypeForUser
{
    [IN]    String Id
    [IN]    String Revision
    [IN]    String User
    [OUT]   Object DeploymentType
};
```

## Parameters

`Id` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Identifier.

`Revision` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Revision.

`User` Data type: `String`

Qualifiers: \[id\("2"\), in\]

User.

`DeploymentType` Data type: `CCM_AppDeploymentType`

Qualifiers: \[id\("3"\), out\]

Deployment type.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
