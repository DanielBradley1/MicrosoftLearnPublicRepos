<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# EnumerateChildren \(containers\)

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## GET /wopi/containers/\(container\_id\)/children

The EnumerateChildren operation enumerates all the immediate children of a given container. Note that paging is deliberately not supported by this operation. Responses are expected to include all immediate children of the container.

### Parameters

- **container\_id** \(*string*\) – A string that specifies a container ID of a container managed by host. This string must be URL safe.

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Request Headers

- *X-WOPI-FileExtensionFilterList* –

  A **string** value that the host must use to filter the returned child files. This header must be a list of comma-separated file extensions with a leading dot \(`.`\). There must be no whitespace and no trailing comma in the string. Wildcard characters are not permitted.

  If this header is included, the host must only return child files whose file extensions match the filter list, based on a case-insensitive match. For example, if this header is set to the value `.doc,.docx`, the host should include only files with the `doc` or `docx` file extension.

  This header value only affects the child files that are returned; it does not have any effect on child containers.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

Note

[**Standard WOPI request and response headers**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers)

In addition to the request/response headers listed here, this operation may also use the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a EnumerateChildren call is [JSON](https://tools.ietf.org/html/rfc4627.html).

All optional values default to the following values based on their type:

| Type | Default value |
| --- | --- |
| Boolean | `false` |
| String | The empty string |
| Integer/Long | Varies; see individual properties for details |
| Array | Empty array |

Important

No properties should be set to `null`. If you do not wish to set a property, simply omit it from the response; the WOPI clients will use the default value in these cases.

### Required response properties

The following properties must be present in all `EnumerateChildren` responses:

- **ChildContainers** - An array of JSON-formatted objects containing the following properties:

  - **Name** - The name of the container without a path. This value should match the *Name* property in a [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) response. Required.
  - **Url** - A URI to the container, including a valid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). Required.

    Caution

    This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and thus has important security implications. See [**Preventing ‘token trading’**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.


  If there are no child containers, this property should be an empty array.

- **ChildFiles** - An array of JSON-formatted objects containing the following properties:

  - **Name** - Should match the [BaseFileName](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#basefilename) property in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). Required.
  - **Size** - Should match the [Size](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#size) property in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). Required.
  - **Url** - A URI to the file, including a valid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). Required.


  Caution


  This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and thus has important security implications. See [**Preventing ‘token trading’**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.


  - **Version** - Should match the [Version](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#version) property in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). Required.
  - **LastModifiedTime** - Should match the [LastModifiedTime](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#lastmodifiedtime) property in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). Optional.


  If there are no child files, this property should be an empty array.


  Sample response:


  ```json
  {
    "ChildContainers": [
      {
        "Url": "http://.../wopi*/containers/<containerId>?access_token=<per_file_token>",
        "Name": "FolderName"
      },
      {
        "Url": "http://.../wopi*/containers/<containerId2>?access_token=<per_file_token2>",
        "Name": "FolderName2"
      }
    ],
    "ChildFiles": [
      {
        "Url": "http://.../wopi*/files/<fileId>?access_token=<per_file_token>",
        "Name": "FileName",
        "Version": "version1",
        "Size": 7,
        "LastModifiedTime": "time last modified"
      }
    ]
  }
  ```
