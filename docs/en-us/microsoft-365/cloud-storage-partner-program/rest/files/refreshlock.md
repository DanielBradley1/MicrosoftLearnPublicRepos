<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# RefreshLock

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![Mobile icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-mobile.png)

The `RefreshLock` operation refreshes the lock on a file.

### POST /wopi/files/\(file\_id\)

The `RefreshLock` operation refreshes the lock on a file by resetting its automatic expiration timer to 30 minutes. The refreshed lock must expire automatically after 30 minutes unless it's modified by a subsequent WOPI operation, such as [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) or [RefreshLock](#refreshlock).

WOPI clients usually make a [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) request to lock a file prior to calling this operation. The WOPI client passes the lock ID established by that previous [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) operation in the **X-WOPI-Lock** request header.

If the file is currently locked and the **X-WOPI-Lock** value doesn't match the lock currently on the file, or if the file is unlocked, the host must do the following:

- Return a *lock mismatch* response \([409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)\)
- Include an **X-WOPI-Lock** response header containing the value of the current lock on the file

In cases where the file is unlocked, the host must set **X-WOPI-Lock** to the empty string.

In cases where the file is locked by someone other than a WOPI client, hosts should still always include the current lock ID in the **X-WOPI-Lock** response header. However, if the current lock ID isn't representable as a WOPI lock \(for example, it's longer than the [maximum lock length](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock-length)\), the **X-WOPI-Lock** response header should be set to the empty string or omitted completely.

For more general information regarding locks, see [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock).

#### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

#### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-Override* – The **string** `REFRESH_LOCK`. This header is required.
- *X-WOPI-Lock* – A **string** provided by the WOPI client that the host must use to identify the existing lock on the file. This header is required.

### Response headers

- *X-WOPI-Lock* – A **string** value identifying the current lock on the file. This header must always be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). It should not be included when responding to the request with [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1).
- *X-WOPI-LockFailureReason* – An optional **string** value indicating the cause of a lock failure. This header might be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). There's no standard for how this string is formatted, and it must only be used for logging purposes.
- *X-WOPI-LockedByOtherInterface* –

  ***Deprecated: Deprecated since version 2015-12-15:*** This header is deprecated and should be ignored by WOPI clients.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) – **X-WOPI-Lock** was not provided or was empty.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found or user unauthorized.
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) – Lock mismatch or locked by another interface. An **X-WOPI-Lock** response header containing the value of the current lock on the file must always be included when using this response code.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).
