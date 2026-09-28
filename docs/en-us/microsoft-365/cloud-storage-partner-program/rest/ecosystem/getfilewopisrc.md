<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getfilewopisrc -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# 🚧 GetFileWopiSrc \(ecosystem\)

## POST /wopi/ecosystem

Caution

This operation *should not* be called by WOPI clients at this time. It is reserved for future use and subject to change.

The GetFileWopiSrc operation is used to convert a host-specific file identifier into a [WopiSrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) value.

The WOPI client passes the host-specific file identifier in the **X-WOPI-HostNativeFileName** header. The host, in turn, returns a WopiSrc URL with an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) appended.

This operation is useful in cases where a WOPI client receives a file identifier that is not a proper WopiSrc, but can be translated into a valid WopiSrc value by the WOPI host.

For example, iOS applications can open files in Microsoft 365 for mobile using URL schemes. However, it may not be feasible for an application to generate a WopiSrc value itself. As long as it can generate a string value that can later be converted to a WopiSrc value by calling this operation, then the application can pass this value and rely on Microsoft 365 for mobile to call this operation to convert the file identifier into a WopiSrc.

Important

While a WOPI host can accept any string value as input, hosts are strongly recommended to support the following values in **X-WOPI-HostNativeFileName**:

- [**HostEditUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl)
- [**HostViewUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostviewurl)
- Any value the host returns in response to a [**GetShareUrl \(files\)**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getshareurl#getshareurl-files) call

Note

This operation is also exposed as a [**shortcut operation**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/shortcuts).

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Request Headers

- *X-WOPI-Override* – The **string** `GET_WOPI_SRC_WITH_ACCESS_TOKEN`. Required.
- *X-WOPI-HostNativeFileName* – A **string** representing the host-specific file identifier for a file.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

Note

In addition to the request/response headers listed here, this operation may also use the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `GetFileWopiSrc` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required property:

- **Url** - A URI that represents a [WopiSrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) value with an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) appended.

  Caution

  This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and thus has important security implications. See [Preventing ‘token trading’](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.

Sample response:

```json
{
  "Url": "http://.../wopi*/[containers|files]/<id>?access_token=<file|container_token>&access_token_ttl=<timestamp>"
}
```
