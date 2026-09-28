<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/getecosystem -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetEcosystem \(containers\)

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## GET \(/wopi/containers/\(container\_id\)/ecosystem\_pointer

The GetEcosystem operation returns the URI for the WOPI server’s Ecosystem endpoint, given a container ID.

Note

[GetEcosystem \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getecosystem) returns the URI for the WOPI server’s Ecosystem endpoint, given a *file* ID.

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

The response to a `GetEcosystem` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required properties:

- **Url** \(*string*\)- A URI for the WOPI server’s Ecosystem endpoint, with an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) appended. A [GET](https://tools.ietf.org/html/rfc7231#section-4.3.1) request to this URL will invoke the [CheckEcosystem](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/checkecosystem) operation.

  Caution

  This property includes an [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and thus has important security implications. See [**Preventing ‘token trading’**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading) for more details.
