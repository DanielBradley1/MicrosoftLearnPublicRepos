<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetCoauthTable

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

Clients can call the `GetCoauthTable` operation to fetch the table that contains information about all the unexpired `Coauth` locks that the various clients acquired. This method doesn't require edit permissions to be called. This method is called frequently.

## Parameters

`file_id` – Required. Passed as part of the endpoint.

## Endpoint

/wopi/files/\(*file\_id*\) – Required.

## Query parameters

`access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request method

POST

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `GET_COAUTH_TABLE`.
- `X-WOPI-CoauthTableVersion` \(string\) – Optional. X-WOPI-CoauthTableVersion value received from previous GetCoauthTable calls indicating the CoauthTable state client already has. If this is same as the latest state on the host, the host must not return any body for GetCoauthTable response and return HTTP code 200 with same CoauthTableVersion in response header. If this header is empty or not matching the current host state \(CoauthTableVersion\), the full CoauthTable would be returned.

## Response headers

- `X-WOPI-CoauthTableVersion` \(string\) – Required. The current version of the CoauthTable based on the host state of the CoauthTable ignoring expiration time for locks. This value must change when the CoauthTable changes. Change here indicates any property of any of the rows returned as part of CoauthTable. Please note that this value should not change if only the expiration time changes for one or more existing CoauthTable entries. This should be returned only as a part of successful response where response code is 200 OK.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set on non-200 OK responses.

## Response body

A mandatory JSON-formatted object that contains the `CoauthTable` property. For the `CoauthTable` structure, see [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table). Returns `CoauthTable` in JSON format and contains an array of entry of each client that has the unexpired `Coauth` locks:

- `CoauthLockId` \(string\) – The ID that's provided by the client.
- `CoauthLockMetadata` \(string\) – Set by the client when it requests the lock.
- `UserFriendlyName` \(string\) – The name of the user, suitable for displaying in the UI. Hosts should be able to populate this value based on the access token that was used to acquire the lock for that client ID.
- `CoauthLockTime` \(uint\) – A long value that indicates the time on the server when the lock was first acquired. The value shouldn't be updated in response to `RefreshCoauthLock` or `GetCoauthLock` when the lock already exists with a specific `CoauthLockId` value. Represented as the number of milliseconds since January 1, 1970 UTC \(the date epoch in JavaScript\).
- `CoauthLockType` \(string\) – `Coauth` or `CoauthExclusive`.

  Note

  `None` is a value that's reserved for future use.

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success. Returns the `CoauthTable` value, even if it's empty.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The required parameters weren't provided.
  - The request was incorrectly formatted.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5)

  - The file doesn't exist.
  - The access token doesn't have edit permissions.

- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)

  - The file is locked by another mechanism.

- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported
- [503 Server Busy](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.4)

## Next steps

Learn about changes in these `CoauthLocks` methods for WOPI coauthoring extensions:

- [GetCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-lock)
- [UnlockCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/unlock-coauth-lock)
- [RefreshCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/refresh-coauth-lock)
