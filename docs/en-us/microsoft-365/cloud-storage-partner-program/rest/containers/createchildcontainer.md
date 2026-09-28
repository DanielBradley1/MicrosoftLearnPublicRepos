<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildcontainer -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# CreateChildContainer

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## POST \(/wopi/containers/\(container\_id\)

The `CreateChildContainer` operation creates a new child container in the provided parent container.

The `CreateChildContainer` operation has two distinct modes: *specific* and *suggested*. The primary difference between the two modes is whether the WOPI client expects the host to use the container name provided exactly \(*specific* mode\), or if the host can adjust the container name in order to make the request succeed \(*suggested* mode\).

Hosts can determine the mode of the operation based on which of the mutually exclusive **X-WOPI-RelativeTarget** \(indicates *specific* mode\) or **X-WOPI-SuggestedTarget** \(indicates *suggested* mode\) request headers is used. We'll describe the expected behavior for each mode in detail below.

### Parameters

- **container\_id** \(*string*\) – A string that specifies a container ID of a container managed by host. This string must be URL safe.

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Request Headers

- *X-WOPI-Override* – The **string** `CREATE_CHILD_CONTAINER`. Required.
- *X-WOPI-SuggestedTarget* –

  A UTF-7 encoded **string** that specifies a full container name. Required.

  The response to a request including this header must never result in a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) or [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). Rather, the host must modify the proposed name as needed to create a new container that is legally named.

  This header must be present if **X-WOPI-RelativeTarget** is not present; the two headers are mutually exclusive. If both headers are present, the host should respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).
- *X-WOPI-RelativeTarget* –

  A UTF-7 encoded **string** that specifies a full container name. The host must not modify the name to fulfill the request.

  If the specified name is illegal, the host must respond with a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1).

  If a container with the specified name already exists, the host must respond with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). When responding with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) for this reason, the host may include an **X-WOPI-ValidRelativeTarget** specifying a container name that is valid.

  This header must be present if **X-WOPI-SuggestedTarget** is not present; the two headers are mutually exclusive. If both headers are present, the host should respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).

### Response Headers

- *X-WOPI-InvalidContainerNameError* – A **string** describing the reason the `CreateChildContainer` operation could not be completed. This header should only be included when the response code is [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1). This string is only used for logging purposes.
- **Status Codes**
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

The response to a `CreateChildContainer` call is [JSON](https://tools.ietf.org/html/rfc4627.html).

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

The following properties must be present in all `CreateChildContainer` responses:

- **ContainerPointer** - A JSON-formatted object containing the following properties:
- **Name** - The name of the container without a path. This value should match the Name property in a [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) response. Required.
- **Url** - A URI to the container, including a valid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). Required.

  Caution

  This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and thus has important security implications. See [**Preventing ‘token trading’**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.

### Other response properties

- **ContainerInfo** - Hosts can optionally include the ContainerInfo property, which should match the [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) response for the newly created container.

  If not provided, the WOPI client will call [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) to retrieve it. Including this property in the response is strongly recommended so that the WOPI client does not need to make an additional call to [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo).

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
