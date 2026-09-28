<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getnewaccesstoken -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetNewAccessToken

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## POST /wopibootstrapper

The GetNewAccessToken operation is used to retrieve a fresh WOPI [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) for a given resource \(i.e. a file or container\), provided the caller has a valid OAuth 2.0 token.

This operation is called by OAuth-capable WOPI clients, such as Microsoft 365 for mobile, to refresh WOPI access tokens when they expire.

### Request Headers

- *X-WOPI-EcosystemOperation* - The string `GET_NEW_ACCESS_TOKEN`. Required.
- *X-WOPI-WopiSrc* - The [WopiSrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) for the file or container. Required.

  Important

  To reduce the likelihood of token spoofing or other unauthorized access, hosts *must* validate the URL provided in the `X-WOPI-WopiSrc` header. The bootstrapper must only provide a WOPI access token if the requested `WopiSrc` exists and the user is authorized to access it. If not, or if the `X-WOPI-WopiSrc` header is not present, the host should return a `404 Not Found` response as described below.

  Important

  In addition, the Microsoft M365 for Mobile apps on both iOS \(version 2.62 and later\) and Android \(version 16.0.15330 and later\) and the Office desktops apps \(applicable for CSPP Plus integrations\) will also validate that the resource specified `by X-WOPI-WopiSrc` is in a trusted domain \(See [Onboarding information](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/onboarding/onboarding)\). Any WOPI requests for resources outside of trusted domains will fail.
- [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – A string in the format `Bearer: <TOKEN>`, where `<TOKEN>` is a Base64-encoded OAuth 2.0 token. If this header is missing, or the token provided is invalid, the host must respond with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) response and include the [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) header as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format).

### Response Headers

- [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) – A **string** value formatted as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format). This header should only be included when responding with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2).

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Authorization failure; when responding with this status code, hosts must include a [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) response header with values as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error

## Response

The response to a `GetNewAccessToken` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required properties:

- **Bootstrap** - The contents of this property should be the response to a [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) call.
- **AccessTokenInfo** - The contents of this property should be a the nested JSON-formatted object with the following properties:
- **AccessToken** - A **string** [access](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) token for the file specified in the **X-WOPI-WopiSrc** request header.
- **AccessTokenExpiry** - A **long** value representing the time that the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) provided in the response will expire. See [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) for more information on how this value is defined.

Sample response:

```json
{
  "Bootstrap": {
    "EcosystemUrl": "http://.../wopi*/ecosystem?access_token=<ecosystem_token>",
    "UserId": "User ID",
    "SignInName": "user@contoso.com",
    "UserFriendlyName": "User Name"
  },
  "AccessTokenInfo": {
    "AccessToken": "1234567890abcdef",
    "AccessTokenExpiry": 1234567890
  }
}
```
