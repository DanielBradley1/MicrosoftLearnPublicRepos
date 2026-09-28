<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/getshareurl -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetShareUrl \(containers\)

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

Note

[GetShareUrl \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getshareurl) returns a Share URL suitable for viewing a shared *file* when launched in a web browser.

## POST \(/wopi/containers/\(container\_id\)

The GetShareUrl operation returns a [Share URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#share-url) that is suitable for viewing a shared container when launched in a web browser. A host can support multiple Share URL types, as described by the [SupportedShareUrlTypes](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportedshareurltypes) property. The **X-WOPI-UrlType** request header contains the Share URL type that should be returned.

If the **X-WOPI-UrlType** header is not present or contains a value that is invalid or not supported by the host, the host should respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).

### Parameters

- **container\_id** \(*string*\) – A string that specifies a container ID of a container managed by host. This string must be URL safe.

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Request Headers

- *X-WOPI-Override* – The **string** `GET_SHARE_URL`. Required.
- *X-WOPI-UrlType* – A **string** indicating what Share URL type to return. Required.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

Note

In addition to the request/response headers listed here, this operation may also use the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `GetShareUrl` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required properties:

- **ShareUrl** - A URI that points to a webpage that allows the user to access the container. Required.

  Note

  Learn more about [Share Url](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#share-url).
