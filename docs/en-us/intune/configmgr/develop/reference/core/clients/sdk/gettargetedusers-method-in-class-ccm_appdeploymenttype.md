<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/gettargetedusers-method-in-class-ccm_appdeploymenttype -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetTargetedUsers Method in Class CCM\_AppDeploymentType

The `GetTargetedUsers` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that retrieves the targeted users of an application deployment type.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetTargetedUsers
{
    [IN]    String Id
    [IN]    String Revision
    [OUT]   String Users[]
};
```

## Parameters

`Id` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Identifier.

`Revision` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Revision.

`Users` Data type: `String Array`

Qualifiers: \[id\("2"\), out\]

Targeted users.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
