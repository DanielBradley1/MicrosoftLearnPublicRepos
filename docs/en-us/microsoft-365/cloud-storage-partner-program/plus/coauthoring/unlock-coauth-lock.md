<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/unlock-coauth-lock -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# UnlockCoauthLock

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

A `Coauth` lock can be released by the clients using UnlockCoauthLock operation on a file. The host will determine the lock entry to be released by using the file ID and `CoauthLockId`.

## Parameters

`file_id` – Required. Passed as part of the endpoint.

## Endpoint

/wopi/files/\(*file\_id*\) – Required.

## Query parameters

`access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request method

POST

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `UNLOCK_COAUTH_LOCK`.
- `X-WOPI-CoauthLockId` \(string\) – Required. A string provided by the client that the host must use to uniquely identify the client for the lock on the file. Size limit: 1,024 ASCII characters.

## Response headers

- `X-WOPI-FailureReason` \(string\) – Optional. Used only for logging purposes. It should be set on non-200 OK responses.

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success. `Coauth` lock was released on the file for the client.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The required parameters weren't provided.
  - The request was incorrectly formatted.
  - The header size wasn't within an acceptable range.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5)

  - The file doesn't exist.
  - The access token doesn't have edit permissions.

- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)

  - The lock doesn't exist.

- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported
- [503 Server Busy](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.4)

## Next steps

Learn about changes in these `CoauthLocks` methods for WOPI coauthoring extensions:

- [GetCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-lock)
- [RefreshCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/refresh-coauth-lock)
- [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table)
