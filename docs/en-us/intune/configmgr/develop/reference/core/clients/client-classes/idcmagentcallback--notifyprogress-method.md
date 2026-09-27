<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyprogress-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMAgentCallback::NotifyProgress Method

The `IDCMAgentCallback::NotifyProgress` method, in Configuration Manager, notifies the caller of progress made on a Desired Configuration Management Agent job.

## Syntax

```
[IDL]
HRESULT NotifyProgress(
     IDCMAgentJob* pJob,
     MessageId msgId
);
```

#### Parameters

`pJob` Data type: `IDCMAgentJob`

Qualifiers: \[in\]

Pointer to the `IDCMAgentJob` object representing the configuration items and their progress.

`msgId` Data type: `MessageId`

Qualifiers: \[in\]

Nothing is returned for this parameter.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface)
