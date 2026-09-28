<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getrootcontainer -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetRootContainer \(bootstrapper\)

![iOS](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-ios-only.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## POST /wopibootstrapper

This operation is equivalent to the [GetRootContainer \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getrootcontainer) operation.

Important

The request/response semantics for this operation differ slightly from its counterpart on the Ecosystem endpoint since it is exposed on the Bootstrapper endpoint, and thus will use OAuth 2.0 access tokens for authorization instead of WOPI access tokens.

### Request Headers

- *X-WOPI-EcosystemOperation* – The **string** `GET_ROOT_CONTAINER`. Required.
- [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – A **string** in the format `Bearer: <TOKEN>` where `<TOKEN>` is a Base64-encoded OAuth 2.0 token. If this header is missing, or the token provided is invalid, the host must respond with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) response and include the [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) header as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format).

### Response Headers

- [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) – A **string** value formatted as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format). This header should only be included when responding with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2).

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Authorization failure; when responding with this status code, hosts must include a [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) response header with values as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

## Response

The response to a GetRootContainer call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required properties:

- **Bootstrap** - The contents of this property should be the response to a [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) call.
- **RootContainerInfo** - The contents of this property should be the response to a [GetRootContainer \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getrootcontainer) call.

Sample response:

```json
{
  "Bootstrap": {
    "EcosystemUrl": "http://.../wopi*/ecosystem?access_token=<ecosystem_token>",
    "UserId": "User ID",
    "SignInName": "user@contoso.com",
    "UserFriendlyName": "User Name"
  },
  "RootContainerInfo": {
    "ContainerPointer" : {
      "Url" : "http://.../wopi*/containers/<containerId>?access_token=<per_container_token>",
      "Name" : "Container Name"
    },
    "ContainerInfo" : {
      "Name" : "Container Name",
      "HostUrl" : "http://contoso/324332",
      "SharingUrl" : "http://contoso/323432/efewos",
      "UserCanCreateChildContainer" : false,
      "UserCanCreateChildFile" : false,
      "UserCanDelete" : false,
      "UserCanRename" : false
    }
  }
}
```
