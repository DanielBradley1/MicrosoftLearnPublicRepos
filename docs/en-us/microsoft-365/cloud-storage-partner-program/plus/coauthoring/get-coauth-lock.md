<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-lock -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetCoauthLock

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

Clients can request a `Coauth` lock by using a `GetCoauthLock` operation on a file. Clients can request `CoauthExclusive` locks if the document isn't exclusively locked and no other client has a `CoauthExclusive` lock.

## Parameters

`file_id` – Required. Passed as part of the endpoint.

## Endpoint

/wopi/files/\(*file\_id*\) – Required.

## Query parameters

`access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request method

POST

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `GET_COAUTH_LOCK`.
- `X-WOPI-CoauthLockId` \(string\) – Required. A string provided by the client that the host must use to uniquely identify the client for the lock on the file. Size limit: 1,024 ASCII characters.
- `X-WOPI-CoauthLockType` \(string\) – Required. The string is `GET_COAUTH_LOCK`. The value can be `Coauth` or `CoauthExclusive`.
- `X-WOPI-CoauthLockMetadata` \(string\) – Optional. Set by the client to any value. If the header is omitted or empty, `CoauthLockMetadata` is set to `empty`. Size limit: 4 KB.
- `X-WOPI-CoauthLockExpirationTimeout` \(uint\) – Required. Represents the timeout duration in seconds for the lock expiration. Can be part of a configuration value on the client side. The host must honor the lock expiration timeout duration that the client provides. The timeout range must be within the values of 1 minute and 1 hour, inclusive of these values.

## Response headers

- `X-WOPI-CoauthTableVersion` \(string\) – Required. The current version of the CoauthTable based on the host state of the CoauthTable ignoring expiration time for locks. This value must change when the CoauthTable changes. Change here indicates any property of any of the rows returned as part of CoauthTable. Please note that this value should not change if only the expiration time changes for one or more existing CoauthTable entries. This should be returned only as a part of successful response where response code is 200 OK.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set on non-200 OK responses.
- `X-WOPI-ConflictingLockUsername` \(string\) – Optional. If the conflict is caused by a WOPI-exclusive lock being held, and if the `UserFriendlyName` associated with the lock is visible \(see `X-WOPI-LockUserVisible`\), this header should contain that `UserFriendlyName` value when it responds to the request with 409 Conflict. This string might be presented to the customer by the Office UX.

## Response body

A mandatory JSON-formatted object that contains the property `CoauthTable`. For the `CoauthTable` structure, see [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table). Returns `CoauthTable` in JSON format and contains array of entry of each client that has the unexpired `Coauth` or `CoauthExclusive` locks.

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success. `Coauth` lock was acquired on the file. The operation succeeds if the file is not exclusively locked by another entity. If a coauth lock already exists with the given `CoauthLockId` and same `CoauthLockType`, the request succeeds. The request in this case updates `CoauthLockMetadata` and `CoauthLockExpirationTimeout`. If a coauth lock already exists with the given `CoauthLockId` but a different `CoauthLockType`, the lock type is switched, except when the request is for a `CoauthExclusive` type lock and another client has `CoauthExclusive` lock.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The required parameters weren't provided.
  - The request was incorrectly formatted.
  - The `CoauthLockExpirationTimeout` that was provided wasn't within an acceptable range.
  - The header size wasn't within an acceptable range.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5)

  - The file wasn't found.
  - The access token doesn't have edit permissions.

- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)

  - The resource is exclusively locked by a different locking mechanism.
  - The resource is exclusively locked by another entity using the same locking mechanism.

- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported
- [503 Server Busy](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.4)

## Next steps

Learn about changes in these `CoauthLocks` methods for WOPI coauthoring extensions:

- [UnlockCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/unlock-coauth-lock)
- [RefreshCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/refresh-coauth-lock)
- [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table)
