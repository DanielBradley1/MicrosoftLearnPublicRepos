<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/renamecontainer -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# RenameContainer

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## POST \(/wopi/containers/\(container\_id\)

The RenameContainer operation renames a container.

### Parameters

- **container\_id** \(*string*\) – A string that specifies a container ID of a container managed by host. This string must be URL safe.

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Request Headers

- *X-WOPI-Override* – The **string** `RENAME_CONTAINER`. Required.
- *X-WOPI-RequestedName* – A UTF-7 encoded **string** that is a container name. Required.

### Response Headers

- *X-WOPI-InvalidContainerNameError* – A **string** describing the reason the RenameContainer operation could not be completed. This header should only be included when the response code is [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1). This string is only used for logging purposes.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) – Specified name is illegal
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) – Target container already exists
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

Note

In addition to the request/response headers listed here, this operation may also use the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `RenameContainer` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required property:

- **Name** \(*string*\) - The name of the renamed container.
