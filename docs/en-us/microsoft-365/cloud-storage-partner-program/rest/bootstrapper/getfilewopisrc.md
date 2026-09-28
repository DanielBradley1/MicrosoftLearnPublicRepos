<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getfilewopisrc -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# 🚧 GetFileWopiSrc \(bootstrapper\)

Warning

This operation should not be called by WOPI clients at this time. It is reserved for future use and subject to change.

## POST /wopibootstrapper

This operation is equivalent to the [🚧 GetFileWopiSrc \(ecosystem\)](#-getfilewopisrc-bootstrapper) operation.

Important

The request/response semantics for this operation differ slightly from its counterpart on the Ecosystem endpoint since it is exposed on the Bootstrapper endpoint, and thus will use OAuth 2.0 access tokens for authorization instead of WOPI access tokens.

- **Request Headers**

  - *X-WOPI-EcosystemOperation* – The **string** `GET_WOPI_SRC_WITH_ACCESS_TOKEN`. Required.
  - *X-WOPI-HostNativeFileName* – A **string** representing the host-specific file identifier for a file.
  - [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – A **string** in the format `Bearer: <TOKEN>` where `<TOKEN>` is a Base64-encoded OAuth 2.0 token. If this header is missing, or the token provided is invalid, the host must respond with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) response and include the [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) header as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format).

- **Response Headers**

  - [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) – A **string** value formatted as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format). This header should only be included when responding with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2).

- **Status Codes**

  - [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
  - [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Authorization failure; when responding with this status code, hosts must include a [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) response header with values as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format)
  - [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
  - [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error

## Response

The response to a GetFileWopiSrc call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required properties:

- **Bootstrap** - The contents of this property should be the response to a [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) operation.
- **WopiSrcInfo** - The contents of this property should be the response to a [🚧 GetFileWopiSrc \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getfilewopisrc) operation.

Sample response:

```json
{
  "Bootstrap": {
    "EcosystemUrl": "http://.../wopi*/ecosystem?access_token=<ecosystem_token>",
    "UserId": "User ID",
    "SignInName": "user@contoso.com",
    "UserFriendlyName": "User Name"
  },
  "WopiSrcInfo": {
    "Url": "http://.../wopi*/[containers|files]/<id>?access_token=<file|container_token>&access_token_ttl=<timestamp>"
  }
}
```
