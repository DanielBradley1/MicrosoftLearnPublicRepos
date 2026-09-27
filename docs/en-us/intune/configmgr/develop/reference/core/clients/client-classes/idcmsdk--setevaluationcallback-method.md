<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--setevaluationcallback-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMSDK::SetEvaluationCallback Method

The `IDCMSDK::SetEvaluationCallback` method, in Configuration Manager, associates a callback object with an existing evaluation job, specified by job ID.

## Syntax

```
[IDL]
HRESULT SetEvaluationCallback(
     JobIdRef  jobId,
     IDCMAgentCallback*  pCallback
);
```

#### Parameters

`jobId` Data type: `JobIdRef`

Qualifiers: \[in\]

ID of the evaluation job to retrieve.

`pCallback` Data type: `IDCMAgentCallback`

Qualifiers: \[in\]

Pointer to an [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface) object. This parameter can be set to `null` if no callback is available.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Remarks

The typical way to use this method is to pass `null` for the `pCallback` parameter.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface) [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface)
