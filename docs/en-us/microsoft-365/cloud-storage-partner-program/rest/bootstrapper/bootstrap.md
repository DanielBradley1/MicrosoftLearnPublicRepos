<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# Bootstrap

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## GET /wopibootstrapper

The Bootstrap operation is used to ‘convert’ an OAuth token into appropriate WOPI [access tokens](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) and provides access to WOPI operations for applications using OAuth tokens, like Microsoft 365 for mobile. For more information see native.

Important

Connections to the bootstrapper must be made using TLS.

### Request Headers

- [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – A **string** in the format `Bearer: <TOKEN>` where `<TOKEN>` is a Base64-encoded OAuth 2.0 token. If this header is missing or blank, or if the token provided is invalid, the host must respond with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) response and include the [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) header, as described in the next section.

### Response Headers

- [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) – A **string** value formatted as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format).
- [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – Must be `application/json` for authenticated responses.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Authorization failure; when responding with this status code, hosts must include a [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) response header with values as described in [WWW-Authenticate response header format](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#www-authenticate-response-header-format)
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error

## Response

The response to a Bootstrap operation differs based on whether it's **authenticated** or **unauthenticated**. When possible, the WOPI client will provide authentication state information, as defined by OAuth 2.0 protocol, in the HTTP header in every request to the Bootstrapper endpoint. This authentication state will be sent in the form of the OAuth 2.0 Access token, and will be contained in the [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) header as described previously.

The host must verify that the provided token is valid. If it isn't, the host must respond as described in the [unauthenticated response](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#unauthenticated-response) section of this article. If the provided token is valid, then the host must respond as described in the [authenticated response](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#authenticated-response) section of this article.

### Authenticated response

When an **authenticated** request \(i.e. a valid OAuth 2.0 access token is included in the [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) HTTP header\) is made to this endpoint, it returns a [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) response with a [JSON](https://tools.ietf.org/html/rfc4627.html) response body. The response must include a single `Bootstrap` property, with the following properties nested within it as needed.

### Required response properties

The following properties must be present in the `Bootstrap` property in all [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) Bootstrap responses:

### EcosystemUrl

A **string** URI for the WOPI server’s Ecosystem endpoint, with a WOPI [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) appended. A [GET](https://tools.ietf.org/html/rfc7231#section-4.3.1) request to this URL will invoke the [CheckEcosystem](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/checkecosystem) operation.

### UserId

A **string** value uniquely identifying the user making the request. This value should match the [UserId](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#userid) value provided in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). This ID is expected to be unique per user and consistent over time. See [Requirements for user identity properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#requirements-for-user-identity-properties) for more information.

### SignInName

A **string** value identifying the user making the request. This value is used to distinguish a user’s account in the event a user has multiple accounts with a given host. This value is often an email address, though it isn't required to be.

### Optional response properties

### UserFriendlyName

A **string** that is the name of the user. This value should match the [UserFriendlyName](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#userfriendlyname) value provided in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

### Sample response

```json
{
  "Bootstrap": {
    "EcosystemUrl": "http://.../wopi*/ecosystem?access_token=<ecosystem_token>",
    "UserId": "User ID",
    "SignInName": "user@contoso.com",
    "UserFriendlyName": "User Name"
  }
}
```

### Unauthenticated response

When an **unauthenticated** request \(i.e. no access token is attached in the [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) HTTP header\) is made to this endpoint, it returns a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) response containing sufficient information to facilitate user authentication with the host.

### WWW-Authenticate response header format

The response must contain sufficient information for a WOPI client to perform the necessary authentication/authorization/token issuance flows with the host’s identity provider, and result in an authenticated call to the same Bootstrapper endpoint.

The information for the successful authentication/authorization/token issuance flows must be returned in the [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) header of the [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) response with type “Bearer.” The information that must be returned in a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) response to an unauthenticated request is as follows:

| Parameter | Value | Required | Example |
| --- | --- | --- | --- |
| Bearer | n/a | Yes | `Bearer` |
| authorization\_uri | The URL of the OAuth2 Authorization Endpoint to begin authentication against as described at: [**RFC 6749#section-3.1**](https://tools.ietf.org/html/rfc6749.html#section-3.1) | Yes | `https://contoso.com/api/oauth2/authorize` |
| tokenIssuance\_uri | The URL of the OAuth2 Token Endpoint where authentication code can be redeemed for an access and \(optional\) refresh token. See Token Endpoint at: [**RFC 6749#section-3.2**](https://tools.ietf.org/html/rfc6749.html#section-3.2) | Yes | `https://contoso.com/api/oauth2/token` |
| providerId | A well-known string \(as registered with Microsoft 365\) that uniquely identifies the host.  <br>Allowed characters: \[a-z, A-Z, 0-9\] | No | `tp_contoso` |
| UrlSchemes | URL scheme your app uses. This is an ordered list by platform. Omit any platforms you don't support. Office will attempt to invoke these URL schemes in order before falling back to the webview auth. | No | {“iOS” : \[“contoso”,”contoso-EMM”\],  <br>“Android” : \[“contoso”,”contoso-EMM”\]  <br>“UWP”: \[“contoso”,”contoso-EMM”\]}  <br>  <br>The value itself must be URL encoded |

These parameters and their values must be formatted as follows:

- Values are contained within double-quotes \(`"`\).
- Contiguous parameters are separated by commas with no comma after the trailing parameter/value pair.
- If no value is known/required for an optional parameter, it may be omitted from the [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) header.
- Multiple instances of [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) HTTP headers may exist in the response to an unauthenticated request to the Bootstrapper endpoint. However, there must be exactly one instance of the [WWW-Authenticate](https://tools.ietf.org/html/rfc7235#section-4.1) header with the `Bearer` qualifier.

### Sample unauthenticated response

```text
HTTP/1.1 401 Unauthorized
<removed for brevity>
WWW-Authenticate: Bearer authorization_uri="https://contoso.com/api/oauth2/authorize",tokenIssuance_uri="https://contoso.com/api/oauth2/token",providerId="tp_contoso", UrlSchemes="%7B%22iOS%22%20%3A%20%5B%22contoso%22%2C%22contoso-EMM%22%5D%2C%20%22Android%22%20%3A%20%5B%22contoso%22%2C%22contoso-EMM%22%5D%2C%20%22UWP%22%3A%20%5B%22contoso%22%2C%22contoso-EMM%22%5D%7D"
Date: Wed, 24 Jun 2015 21:52:44 GMT
```
