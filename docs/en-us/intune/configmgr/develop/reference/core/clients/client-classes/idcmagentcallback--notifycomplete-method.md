<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifycomplete-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMAgentCallback::NotifyComplete Method

The `IDCMAgentCallback::NotifyComplete` method, in Configuration Manager, notifies the caller that a Desired Configuration Management Agent job has completed.

## Syntax

```
[IDL]
HRESULT NotifyComplete(
     IDCMAgentJob* pJob
);
```

#### Parameters

`pJob` Data type: `IDCMAgentJob`

Qualifiers: \[in\]

Pointer to the `IDCMAgentJob` object representing the configuration items and their progress.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface)
