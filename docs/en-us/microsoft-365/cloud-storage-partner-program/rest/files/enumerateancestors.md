<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/enumerateancestors -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# EnumerateAncestors \(files\)

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The `EnumerateAncestors` operation represents an ancestry file or folder being operated on via WOPI operations. A host must issue a unique ID for any file used by a WOPI client. The client will, in turn, include the file ID when making requests to the WOPI host. Thus, a host must be able to use the file ID to locate a particular file. For more information on File ID strings and requirements for integration, see [Key concepts](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts).

Note

[**EnumerateAncestors \(containers\)**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumerateancestors)

## GET /wopi/files/\(file\_id\)/ancestry

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Response headers

- *X-WOPI-EnumerationIncomplete* –

  An optional header indicating that the enumeration of the container’s ancestry is incomplete. If set, the value of this header must be the string `true`.

  A WOPI client might choose to issue additional `EnumerateAncestors` requests to complete the enumeration.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found or user unauthorized.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `EnumerateAncestors` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required properties:

- **AncestorsWithRootFirst** - An array of JSON-formatted objects containing the following properties:

  - **Name** - The name of the container without a path. This value should match the Name property in a [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) response. This value is required.
  - **Url** - A URL to the container, including a valid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). This property is required.


  Caution


  This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) so it has important security implications. See [**Preventing ‘token trading’**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.


  The array must always be ordered such that the ancestor closest to the root is the first element.


  If there are no ancestor containers, this property should be an empty array.


  Consider a file in the following container hierarchy: `/root/grandparent/parent/myfile.docx`. When called on this file, the EnumerateAncestors operation should return the following:


  ```json
  {
    "AncestorsWithRootFirst": [
      {
        "Url": "http://.../wopi*/containers/<containerId>?access_token=<per_container_token>",
        "Name": "root"
      },
      {
        "Url": "http://.../wopi*/containers/<containerId2>?access_token=<per_container_token2>",
        "Name": "grandparent"
      },
      {
        "Url": "http://.../wopi*/containers/<containerId3>?access_token=<per_container_token3>",
        "Name": "parent"
      }
    ]
  }
  ```
