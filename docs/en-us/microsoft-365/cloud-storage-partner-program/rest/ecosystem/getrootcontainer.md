<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getrootcontainer -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetRootContainer \(ecosystem\)

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## GET /wopi/ecosystem/root\_container\_pointer

The GetRootContainer operation returns the root container. A WOPI client can use this operation to get a reference to the root container, from which the client can call [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren) to navigate a container hierarchy.

Note

This operation is also exposed as a [**shortcut operation**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/shortcuts).

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

Note

In addition to the request/response headers listed here, this operation may also use the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a GetRootContainer call is [JSON](https://tools.ietf.org/html/rfc4627.html).

All optional values default to the following values based on their type:

| Type | Default value |
| --- | --- |
| Boolean | `false` |
| String | The empty string |
| Integer/Long | Varies; see individual properties for details |
| Array | Empty array |

Important

No properties should be set to `null`. If you do not wish to set a property, simply omit it from the response; WOPI clients will use the default value in these cases.

### Required response properties

The following properties must be present in all GetRootContainer responses:

- **ContainerPointer** - A JSON-formatted object containing the following properties:
- **Name** The name of the container without a path. This value should match the *Name* property in a [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) response. Required.
- **Url** - A URI to the container, including a valid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). Required.

  Caution

  This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and thus has important security implications. See [**Preventing ‘token trading’**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.

### Other response properties

- **ContainerInfo** - Hosts can optionally include the ContainerInfo property, which should match the [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) response for the root container.

  If not provided, the WOPI client will call [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) to retrieve it. We strongly recommend including this property in the response so that the WOPI client does not need to make an additional call to [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo).

Sample response:

```json
{
  "ContainerPointer" : {
    "Url" : "http://.../wopi*/containers/<containerId>?access_token=<per_container_token>",
    "Name" : "Container Name"
  },
  "ContainerInfo" : {
    "Name" : "Container Name",
    "HostUrl" : "",
    "SharingUrl" : "",
    "UserCanCreateChildContainer" : false,
    "UserCanCreateChildFile" : false,
    "UserCanDelete" : false,
    "UserCanRename" : false
  }
}
```
