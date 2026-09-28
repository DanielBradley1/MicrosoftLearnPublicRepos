<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/checkecosystem -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# CheckEcosystem

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## GET /wopi/ecosystem

The CheckEcosystem operation is similar to the the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) operation, but does not require a file or container ID.

### Query Parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host will use to determine whether the request is authorized.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error

## Response

The response to a CheckEcosystem call is [JSON](https://tools.ietf.org/html/rfc4627.html).

All optional values default to the following values based on their type:

| Type | Default value |
| --- | --- |
| Boolean | `false` |
| String | The empty string |
| Integer/Long | Varies; see individual properties for details |
| Array | Empty array |

Important

No properties should be set to `null`. If you do not wish to set a property, simply omit it from the response; WOPI clients will use the default value in these cases.

### Optional response properties

- **SupportsContainers** - Should match the [SupportsContainers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportscontainers) property in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

  Note

  Since all properties in the CheckEcosystem response are optional, an empty JSON response is valid.
