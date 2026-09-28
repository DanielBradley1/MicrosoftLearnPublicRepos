<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getshareurl -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetShareUrl \(files\)

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The GetShareUrl operation returns a share URL that's suitable for viewing a shared file when launched in a web browser.

Note

[**GetShareUrl \(containers\)**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/getshareurl)

## POST \(/wopi/files/\(file\_id\)

The GetShareUrl operation returns a [Share URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#share-url) that's suitable for viewing a shared file when launched in a web browser. A host can support multiple Share URL types, as described by the [SupportedShareUrlTypes](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportedshareurltypes) property. The **X-WOPI-UrlType** request header contains the Share URL type that should be returned.

If the **X-WOPI-UrlType** header is not present or contains a value that's invalid or not supported by the host, the host should respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-Override* – The **string** `GET_SHARE_URL`. This header is required.
- *X-WOPI-UrlType* – A **string** indicating what Share URL type to return. This header is required.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

Note

[**Standard WOPI request and response headers**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers)

In addition to the request/response headers listed here, this operation may also use the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `GetShareUrl` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required property:

- **ShareUrl** - A URL that points to a webpage, which lets a user access the file. This URL is required. For more information, see [**Share URL**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#share-url).
