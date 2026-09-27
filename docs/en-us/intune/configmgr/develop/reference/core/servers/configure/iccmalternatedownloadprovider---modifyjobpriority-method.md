<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobpriority-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# ICcmAlternateDownloadProvider : ModifyJobPriority Method

The **ICcmAlternateDownloadProvider::ModifyJobPriority** method, in Configuration Manager, instructs the provider to modify the priority for a given job.

## Syntax

```
HRESULT ModifyJobPriority(
        [in] REFGUID JobID,
        [in] CCM_DTS_PRIORITY Priority
        );
```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: \[in\]

The job on which to take action.

`Priority` Data type: `CCM_DTS_PRIORITY`

Qualifiers: \[in\]

The new priority.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Remarks

Note

An error should be returned if the job is not found or if modification of the priority failed. If any changes are required to make the guarantees described above on the comments on CCM\_DTS\_PRIORITY, the provider must make them. If the provider cannot honor that guarantee, it should report an error from this function.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
