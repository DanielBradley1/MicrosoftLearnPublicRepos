<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobsource-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# ICcmAlternateDownloadProvider: ModifyJobSource Method

The **ICcmAlternateDownloadProvider::ModifyJobSource** method, in Configuration Manager, instructs the provider to modify the source location for a given job.

## Syntax

```
HRESULT ModifyJobSource(
            REFGUID JobID,
            LPCWSTR szSourceURL,
            DWORD dwFlags
    );
```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: \[in\]

The job on which to take action.

`szSourceURL` Data type: `LPCWSTR`

Qualifiers: \[in\]

The new source location.

`dwFlags` Data type: `DWORD`

Qualifiers: \[in\]

The new job flags. This can be ignored by alternate providers.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Remarks

Note

An error should be returned if the job is not found or if modification of the source location failed or if the provider is using the old location and cannot handle the new location.

If the provider is not using the source location provided in the call to **ICcmAlternateDownloadProvider::DownloadContent** method, it can safely ignore this call, but it should not report an error.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
