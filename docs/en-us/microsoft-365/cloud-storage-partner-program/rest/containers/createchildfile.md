<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildfile -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# CreateChildFile

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## POST /wopi/containers/\(container\_id\)

The `CreateChildFile` operation creates a new file in the provided container. **The resulting file must be zero bytes in length.**

The `CreateChildFile` operation has two distinct modes: *specific* and *suggested*. The primary difference between the two modes is whether the WOPI client expects the host to use the file name provided exactly \(*specific* mode\), or if the host can adjust the file name in order to make the request succeed \(*suggested* mode\).

Hosts can determine the mode of the operation based on which of the mutually exclusive **X-WOPI-RelativeTarget** \(indicates *specific* mode\) or **X-WOPI-SuggestedTarget** \(indicates *suggested* mode\) request headers is used. We'll describe the expected behavior for each mode in detail below.

Note that a file matching the target name might be locked, and in *specific* mode, the host must respond with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) and include a **X-WOPI-Lock** response header as described below.

### Parameters

- **container\_id** \(*string*\) – A string that specifies a container ID of a container managed by host. This string must be URL safe.

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Request Headers

- *X-WOPI-Override* – The **string** `CREATE_CHILD_FILE`. Required.
- *X-WOPI-SuggestedTarget* –

  A UTF-7 encoded **string** specifying either a file extension or a full file name, including the file extension. Hosts can differentiate between full file names and extensions as follows:

  - If the string begins with a period \(`.`\), it's a file extension.
  - Otherwise, it's a full file name.

    If only the extension is provided, the name of the initial file without extension should be combined with the extension to create the proposed name.

    The response to a request including this header must never result in a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) or [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). Rather, the host must modify the proposed name as needed to create a new file that is both legally named and does not overwrite any existing file, while preserving the file extension.

    This header must be present if **X-WOPI-RelativeTarget** is not present; the two headers are mutually exclusive. If both headers are present, the host should respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).

- *X-WOPI-RelativeTarget* –

  A UTF-7 encoded **string** that specifies a full file name including the file extension. The host must not modify the name to fulfill the request.

  If the specified name is illegal, the host must respond with a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1).

  If a file with the specified name already exists, the host must respond with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10), unless the **X-WOPI-OverwriteRelativeTarget** request header is set to `true`. When responding with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) for this reason, the host may include an **X-WOPI-ValidRelativeTarget** specifying a file name that is valid.

  If the **X-WOPI-OverwriteRelativeTarget** request header is set to `true` and a file with the specified name already exists and is locked, the host must respond with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) and include an **X-WOPI-Lock** response header containing the value of the current lock on the file.

  This header must be present if **X-WOPI-SuggestedTarget** is not present; the two headers are mutually exclusive. If both headers are present, the host should respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).
- *X-WOPI-OverwriteRelativeTarget* –

  A **Boolean** value that specifies whether the host must overwrite the file name if it exists. The default value is `false`. In other words, if **X-WOPI-OverwriteRelativeTarget** is not explicitly included on the request, hosts must behave as though its value is `false`.

  This header is only valid if the **X-WOPI-RelativeTarget** is also included on the request. It must be ignored in all other cases.

  If the user is not authorized to overwrite the target file, the host must respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).

### Response Headers

- *X-WOPI-InvalidFileNameError* – A **string** describing the reason the `CreateChildFile` operation could not be completed. This header should only be included when the response code is [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1). This string is only used for logging purposes.
- *X-WOPI-ValidRelativeTarget* – A UTF-7 encoded **string** that specifies a full file name including the file extension. This header may be used when responding with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10), because a file with the requested name already exists, or when responding with a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1), because the requested name contained invalid characters. If this response header is included, the WOPI client should automatically retry the `CreateChildFile` operation using the contents of this header as the **X-WOPI-RelativeTarget** value and should not display an error message to the user.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) – Specified name is illegal
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) – Target file already exists
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported

Note

In addition to the request/response headers listed here, this operation may also use the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `CreateChildFile` call is [JSON](https://tools.ietf.org/html/rfc4627.html).

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

The following properties must be present in all `CreateChildFile` responses:

- **Name** - The **string** name of the file, including extension, without a path.
- **Url** - A **string** URI of the form `http://server/<...>/wopi/files/(file_id)?access_token=(access token)`, of the newly created file on the host. This URL is the [WOPISrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) for the new file with an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) appended. Or, stated differently, it is the URL to the host’s Files endpoint for the new file, along with an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). A [GET](https://tools.ietf.org/html/rfc7231#section-4.3.1) request to this URL will invoke the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) operation.

  Caution

  This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and thus has important security implications. See [**Preventing ‘token trading’**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.

### Optional response properties

- **HostViewUrl** - The [HostViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostviewurl), as a **string**, for the newly created file. This should match the value returned in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
- **HostEditUrl** A URI to the [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#wopi-host--wopi-server) that loads the `editnew` WOPI action.

  The [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl), as a **string**, for the newly created file. This should match the value returned in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
