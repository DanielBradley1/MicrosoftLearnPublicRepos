<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/deletefile -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# DeleteFile

Optional for: ![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The `DeleteFile` operation deletes a file from a host.

Note

This WOPI operation isn't required to integrate with Office for the web or Microsoft 365 for mobile at this time.

## POST /wopi/files/\(file\_id\)

The `DeleteFile` operation deletes a file from a host.

If the file is currently locked, the host should return a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) and include an **X-WOPI-Lock** response header containing the value of the current lock on the file. If the current lock ID is not representable as a WOPI lock \(for example, it's longer than the [maximum lock length](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock-length)\), the host should return a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) and set the **X-WOPI-Lock** response header to the empty string or omit it completely.

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-Override* – The **string** `DELETE`. Required.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found or user unauthorized.
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) – Lock mismatch or locked by another interface. You must include an **X-WOPI-Lock** response header containing the value of the current lock on the file when using this response code.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).
