<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---resume-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# ICcmAlternateDownloadProvider : Resume Method

The **ICcmAlternateDownloadProvider::Resume** method, in Configuration Manager, instructs the provider to resume a given job.

## Syntax

```
HRESULT Resume(
            REFGUID JobID
    );
```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: \[in\]

The job on which to take action.

## Remarks

Note

The provider must support Resume being called on a job that is not suspended. In that case, it should simply do nothing and not report an error. An error should be returned if the job is not found or if resuming failed.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
