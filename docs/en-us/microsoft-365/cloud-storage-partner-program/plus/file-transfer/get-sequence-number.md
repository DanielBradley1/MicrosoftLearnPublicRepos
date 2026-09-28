<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-sequence-number -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetSequenceNumber

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

POST /wopi/files/\(file\_id\)

The `GetSequenceNumber` operation retrieves the sequence number of the file on the host.

## Parameters

- `file_id` \(string\) – Required. A string that specifies the file ID of a file managed by the host. This string must be URL safe.

## Query parameters

- `access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `GET_SEQUENCE_NUMBER`.

## Response headers

- `X-WOPI-SequenceNumber` \(integer\) – Required. An integer value that indicates the latest state of the file on the host. The value should be greater than 0, and should be increased if the host file is updated.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set on non-200 OK responses.

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token.
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

## Next steps

[File content data model](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/file-content-data-model)
