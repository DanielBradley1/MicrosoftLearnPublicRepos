<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sendnotifyerrortoctm-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# SendNotifyErrorToCTM Method

The **SendNotifyErrorToCTM** method, in Configuration Manager, notifies Content Transfer Manager of errors.

## Syntax

```
HRESULT stdcall SendNotifyErrorToCTM(
    LPCWSTR szEndpoint,
    LPCWSTR szID,
    LPCWSTR szClientData,
    HRESULT hrErrorCode,
    LPCWSTR szErrorMessage
);
```

#### Parameters

`szEndpoint` Data type: LPCWSTR

Qualifiers: \[in\]

The notification endpoint. This was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** \(szNotifyEndpoint\).

`szID` Data type: LPCWSTR

Qualifiers: \[in\]

The job to which the notification corresponds. This is the GUID originally returned by **ICcmAlternateDownloadProvider::DownloadContent**.

`szClientData` Data type: LPCWSTR

Qualifiers: \[in\]

The client-specific data that was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** \(szNotifyData.\)

`hrErrorCode` Data type: HRESULT

Qualifiers: \[in\]

The failure code to report.

`szErrorMessage` Data type: LPCWSTR

Qualifiers: \[in\]

An extended status message. Must not be NULL.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
