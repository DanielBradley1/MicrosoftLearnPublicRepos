<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/identity/tokenissuance -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Token issuance URL requirements

This section describes requirements for your token issuance endpoint \([**RFC 6749#section-3.2**](https://tools.ietf.org/html/rfc6749.html#section-3.2)\):

- You must set the [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) header to `application/json`
- You should specify the OAuth2 access token expiration via the `expires_in` property, in seconds.
- If your access tokens do not expire, set the OAuth2 access to a value of 0 \(zero\).

Example Response Body:

```text
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8

{
    "access_token":"123abcdefg",
    "token_type": "bearer",
    "expires_in": "86400"
}
```
