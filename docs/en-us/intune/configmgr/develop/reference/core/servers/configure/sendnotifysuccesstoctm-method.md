<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sendnotifysuccesstoctm-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# SendNotifySuccessToCTM Method

The **SendNotifySuccessToCTM** method notifies Content Transfer Manager of the success of a job.

Note

When calling this method, the number of bytes/files transferred \(`szBytesTransferred`\) should equal the total \(`szBytesTotal`\).

## Syntax

```
HRESULT stdcall SendNotifySuccessToCTM(
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

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
