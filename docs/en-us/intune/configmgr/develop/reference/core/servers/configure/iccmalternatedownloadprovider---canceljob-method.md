<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---canceljob-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# ICcmAlternateDownloadProvider : CancelJob Method

The **ICcmAlternateDownloadProvider::CancelJob** method, in Configuration Manager, cancels a job.

Note

An error should be returned if the job is not found or if cancellation failed.

## Syntax

```
HRESULT CancelJob(
            REFGUID JobID
    );
```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: \[in\]

The job upon which to take action.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
