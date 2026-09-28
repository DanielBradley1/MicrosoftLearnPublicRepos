<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# UnlockAndRelock

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The `UnlockAndRelock` operation releases a lock on a file, and then immediately places a new lock on the file.

### POST /wopi/files/\(file\_id\)

The `UnlockAndRelock` operation releases a lock on a file, and then immediately places a new lock on the file.

Important

This operation must be atomic.

`UnlockAndRelock` is similar semantically to the [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) operation. The two operations share the same **X-WOPI-Override** value. So, hosts must differentiate the two operations based on the presence, or lack of, the **X-WOPI-OldLock** request header.

Unlike the [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) operation, the `UnlockAndRelock` operation passes the current expected lock ID in the **X-WOPI-OldLock** request header. The **X-WOPI-Lock** value is the lock ID for the new lock.

If the file is currently locked and the **X-WOPI-OldLock** value doesn't match the lock currently on the file, or if the file is unlocked, the host must:

- Return a *lock mismatch* response \([409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)\)
- Include an **X-WOPI-Lock** response header containing the value of the current lock on the file

In cases where the file is unlocked, the host must set **X-WOPI-Lock** to the empty string.

In cases where the file is locked by someone other than a WOPI client, hosts should still always include the current lock ID in the **X-WOPI-Lock** response header. However, if the current lock ID isn't representable as a WOPI lock \(for example, it's longer than the [maximum lock length](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock-length)\), you should set the **X-WOPI-Lock** response header to the empty string or omitted completely.

For more general information about locks, see [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock).

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-Override* – The **string** `LOCK`. Required.
- *X-WOPI-Lock* – A **string** provided by the WOPI client that the host must use to identify the new lock on the file. The maximum length of a lock ID is 1024 ASCII characters. Required.
- *X-WOPI-OldLock* – A **string** provided by the WOPI client that is the existing lock on the file. Required. If **X-WOPI-OldLock** is not provided, the request is identical to a [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock) request.

### Response headers

- *X-WOPI-Lock* – A **string** value identifying the current lock on the file. This header must always be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). It should not be included when responding to the request with [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1).
- *X-WOPI-LockFailureReason* – An optional **string** value indicating the cause of a lock failure. This header Might be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). There's no standard for how this string is formatted, and it must only be used for logging purposes.
- *X-WOPI-LockedByOtherInterface* –

  ***Deprecated: Deprecated since version 2015-12-15:*** This header is deprecated and should be ignored by WOPI clients.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) – **X-WOPI-Lock** was not provided or was empty.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) – Lock mismatch or locked by another interface. You must include an **X-WOPI-Lock** response header containing the value of the current lock on the file when using this response code.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).
