<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/evaluateallpolicies-method-in-class-ccm_applicationpolicy -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# EvaluateAllPolicies Method in Class CCM\_ApplicationPolicy

The `EvaluateAllPolicies` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that evaluated all policies.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 EvaluateAllPolicies
{
    [IN]    Boolean IsEnforceAction
    [OUT]   String JobIdUser
    [OUT]   String JobIdMachine
};
```

## Parameters

`IsEnforceAction` Data type: `Boolean`

Qualifiers: \[id\("0"\), in\]

`True` if the action is enforced.

`JobIdUser` Data type: `String`

Qualifiers: \[id\("1"\), out\]

Job identifier of a user policy.

`JobIdMachine` Data type: `String`

Qualifiers: \[id\("2"\), out\]

Job identifier of a machine policy.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
