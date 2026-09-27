<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sendnotifyprogresstoctm-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SendNotifyProgressToCTM Method

The **SendNotifyProgressToCTM** method notifies Content Transfer Manager of the progress of a job.

## Syntax

```
HRESULT stdcall SendNotifyProgressToCTM(
    LPCWSTR szProgressType,
    LPCWSTR szEndpoint,
    LPCWSTR szID,
    LPCWSTR szClientData,
    LPCWSTR szBytesTotal,
    LPCWSTR szBytesTransferred,
    ULONG ulFilesTotal,
    ULONG ulFilesTransferred
);
```

#### Parameters

`szProgressType` Data type: LPCWSTR

Qualifiers: \[in\]

Either one of the S\_DTS\_\* constants for status changes or NULL/empty string for a bytes progress only.

`szEndpoint` Data type: LPCWSTR

Qualifiers: \[in\]

The notification endpoint. This was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** \(szNotifyEndpoint\).

`szID` Data type: UInt32

Qualifiers: \[in\]

The job to which the notification corresponds. This is the GUID originally returned by **ICcmAlternateDownloadProvider::DownloadContent**.

`szClientData` Data type: LPCWSTR

Qualifiers: \[in\]

The client-specific data that was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** \(szNotifyData\).

`szBytesTotal` Data type: LPCWSTR

Qualifiers: \[in\]

The total number of bytes in the job.

`szBytesTransferred` Data type: LPCWSTR

Qualifiers: \[in\]

The number of bytes transferred so far.

`ulFilesTotal` Data type: ULONG

Qualifiers: \[in\]

The total number of files in the job.

`ulFilesTransferred` Data type: ULONG

Qualifiers: \[in\]

The number of files transferred so far.

## Remarks

If the totals aren't yet known, pass 0 for the values. Once the provider has determined the total byte and file count, those values should be used.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
