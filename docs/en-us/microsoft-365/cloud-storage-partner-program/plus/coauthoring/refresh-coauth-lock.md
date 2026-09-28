<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/refresh-coauth-lock -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# RefreshCoauthLock

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

A client can refresh a `Coauth` lock by using the `RefreshCoauthLock` operation on a file. The host determines the lock entry to be refreshed by using the file ID and the `CoauthLockId` value.

This call works only if there is an unexpired lock reference for the `Coauth` or `CoauthExclusive` lock.

## Parameters

`file_id` – Required. Passed as part of the endpoint.

## Endpoint

/wopi/files/\(*file\_id*\) – Required.

## Query parameters

`access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request method

POST

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `REFRESH_COAUTH_LOCK`.
- `X-WOPI-CoauthLockId` \(string\) – Required. A string provided by the client that the host must use to uniquely identify the client for the lock on the file. Size limit: 1,024 ASCII characters.
- `X-WOPI-CoauthLockExpirationTimeout` \(uint\) – Required. Represents the timeout duration for the lock expiration in seconds. The value can be part of a configuration value on the client side. The host must honor the lock expiration timeout duration the client provides. The timeout range must be within the values of 1 minute and 1 hour, inclusive of these values.
- `X-WOPI-CoauthLockMetadata` \(string\) – Optional. Set by the client to any value. If the header is omitted or empty, the `CoauthLockMetadata` value remains unchanged. If the header is set to a non-empty string, `CoauthLockMetadata` is overwritten with that value. Size limit: 4 KB.

## Response headers

- `X-WOPI-CoauthTableVersion` \(string\) – Required. The current version of the CoauthTable based on the host state of the CoauthTable ignoring expiration time for locks. This value must change when the CoauthTable changes. Change here indicates any property of any of the rows returned as part of CoauthTable. Please note that this value should not change if only the expiration time changes for one or more existing CoauthTable entries. This should be returned only as a part of successful response where response code is 200 OK.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set on non-200 OK responses.

## Response body

A mandatory JSON-formatted object that contains the `CoauthTable` property. For the `CoauthTable` structure, see [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table). Returns `CoauthTable` in JSON format and contains an array of entry of each client that has the unexpired `Coauth` locks.

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success. `Coauth` lock was refreshed on the file for the client.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The required parameters weren't provided.
  - The request was incorrectly formatted.
  - The `CoauthLockExpirationTimeout` provided was not within an acceptable range.
  - The header size wasn't within the acceptable range.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5)

  - The file wasn't found.
  - The access token doesn't have edit permissions.

- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)

  - The lock doesn't exist.

- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported
- [503 Server Busy](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.4)

## Next steps

Learn about changes in these `CoauthLocks` methods for WOPI coauthoring extensions:

- [GetCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-lock)
- [UnlockCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/unlock-coauth-lock)
- [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table)
