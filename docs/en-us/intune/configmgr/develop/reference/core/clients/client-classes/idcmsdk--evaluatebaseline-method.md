<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--evaluatebaseline-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMSDK::EvaluateBaseline Method

The `IDCMSDK::EvaluateBaseline` method, in Configuration Manager, runs the discover operation for the specified baseline configuration item.

## Syntax

```
[IDL]
HRESULT EvaluateBaseline(
     const struct CIDetectInfo* pInfo,
     IDCMAgentCallback*  pCallback,
     BOOL  bForce,
     JobId*  pJobId
);
```

#### Parameters

`pInfo` Data type: `struct`

Qualifiers: \[in\]

Pointer to a [CIDetectInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure) containing information about the baseline configuration item.

`pCallback` Data type: `IDCMAgentCallback`

Qualifiers: \[in\]

Pointer to an [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface) object that is used to notify the agent of the progress, completion, or failure of the operation.

`bForce` Data type: `BOOL`

Qualifiers: \[in\]

`true` if the method is to force the evaluation scan of the baseline configuration item. This value requires administrator privileges.

A setting of `false` for this parameter allows the scan to run, but it doesn't run if the last evaluation of the baseline met the Desired Configuration Management TimeToLive threshold.

`pJobId` Data type: `JobId`

Qualifiers: \[out\]

Pointer to the ID of the new Desired Configuration Management Agent job for the baseline configuration item.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface) [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface) [CIDetectInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure)
