<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo -->
<!-- Sitemap-Last-Modified: 2023-07-12 -->

# CheckContainerInfo

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## GET /wopi/containers/\(container\_id\)

The `CheckContainerInfo` operation is similar to the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) operation, but operates on containers instead of files. `CheckContainerInfo` returns information about a container and a user’s permissions on that container.

### Parameters

- **container\_id** \(*string*\) – A string that specifies a container ID of a container managed by host. This string must be URL safe.

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

The response to a `CheckContainerInfo` call is [JSON](https://tools.ietf.org/html/rfc4627.html).

All optional values default to the following values based on their type:

| Type | Default value |
| --- | --- |
| Boolean | `false` |
| String | The empty string |
| Integer/Long | Varies; see individual properties for details |
| Array | Empty array |

Important

No properties should be set to `null`. If you do not wish to set a property, simply omit it from the response and WOPI clients will use the default value.

### Required response properties

The following properties must be present in all `CheckContainerInfo` responses:

- **Name** - The name of the container without a path. This value will be displayed in the WOPI client UI.

### Other response properties

- **HostUrl** - A URI to a webpage for the container.
- **IsAnonymousUser** \(*Boolean*\) - A Boolean value indicating whether the user is authenticated with the host or not. This should match the [IsAnonymousUser](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#isanonymoususer) value returned in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
- **IsEduUser** \(*Boolean*\) - A Boolean value indicating whether the user is an education user or not. This should match the [IsEduUser](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#iseduuser) value returned in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
- **LicenseCheckForEditIsEnabled** \(*Boolean*\) - A Boolean value indicating whether the user is a business user or not. This should match the [LicenseCheckForEditIsEnabled](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#licensecheckforeditisenabled) value returned in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
- **SharingUrl** - A URI to a webpage to allow the user to control sharing of the container. This is analogous to the [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
- **SupportedShareUrlTypes** - An array of strings containing the [Share URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#share-url) types the host supports. The types indicate the sharing options available for the container itself, and not on the files in the container.

  These types can be passed in the **X-WOPI-UrlType** request header to signify which Share URL type to return for the [GetShareUrl \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/getshareurl#getshareurl-containers) operation.

  | ***Possible Values*** | ***Description*** |
  | --- | --- |
  | **ReadOnly** | This type of Share URL allows users to view the container using the URL, but does not give them permission to make changes to the container. |
  | **ReadWrite** | This type of Share URL allows users to both view and make changes to the container using the URL. |

- **UserCanCreateChildContainer** \(*Boolean*\) - A Boolean value that indicates the user has permission to create a new container in the container.
- **UserCanCreateChildFile** \(*Boolean*\) - A Boolean value that indicates the user has permission to create a new file in the container.
- **UserCanDelete** \(*Boolean*\) - A Boolean value that indicates the user has permission to delete the container.
- **UserCanRename** \(*Boolean*\) - A Boolean value that indicates the user has permission to rename the container.
