<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetFile

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The `GetFile` operation retrieves a file from a host.

### GET /wopi/files/\(file\_id\)/contents

The `GetFile` operation retrieves a file from a host.

Tip

By default, Microsoft 365 for the web uses the GetFile WOPI request to retrieve files from the host. However, hosts can override this behavior by providing a direct URL to the file using the [**FileUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileurl) property in the [**CheckFileInfo**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response.

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-MaxExpectedSize* – An **integer** specifying the upper bound of the expected size of the file being requested. Optional. The host should use the maximum value of a 4-byte integer if this value isn't set in the request. If the file requested is larger than this value, the host must respond with a [412 Precondition Failed](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.13).

### Response headers

- *X-WOPI-ItemVersion* – An optional **string** value indicating the version of the file. Its value should be the same as [Version](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#version) value in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

### Response body

The response body must be the full binary contents of the file.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found or user unauthorized.
- [412 Precondition Failed](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.13) – File is larger than **X-WOPI-MaxExpectedSize**.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).
