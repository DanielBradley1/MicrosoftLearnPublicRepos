<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/identity/specifytokenissuance -->
<!-- Sitemap-Last-Modified: 2023-03-09 -->

# Post-Authorization token endpoint

The token endpoint URL \([RFC 6749#section-3.2](https://tools.ietf.org/html/rfc6749.html#section-3.2)\) is normally obtained from the initial unauthenticated call described in the [Bootstrap OAuth2](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/identity/bootstrapper) topic.

If the token endpoint URL cannot be determined before the end user has completed the sign-in process, an alternative token endpoint URL may be supplied.

This is done via a `tk=` URL parameter appended to the value of the [Location](https://tools.ietf.org/html/rfc7231#section-7.1.2) header from the [302 Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.3) response at the end of the sign-in flow.

Important

The `tk=` parameter name is **case-sensitive** and its contents must be URL encoded.

For example, to return the following information:

| Information | Value |
| --- | --- |
| Redirection URI | `https://localhost` |
| Authorization code \([RFC 6749#section-4.1.2](https://tools.ietf.org/html/rfc6749.html#section-4.1.2)\) | "abcdefg" |
| Token endpoint URL | `https://contoso.com/api/token/?extra=stuff` |

The [Location](https://tools.ietf.org/html/rfc7231#section-7.1.2) header in the [302 Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.3) response would be:

`Location: https://localhost?code=abcdefg&tk=https%3A%2F%2Fcontoso.com%2Fapi%2Ftoken%2F%3Fextra%3Dstuff`

As a result, all calls to the token endpoint for obtaining access token via authentication-code exchange \(or refresh flows using the refresh token\) will hit this URL instead of the one initially returned as described in the [Bootstrap OAuth2](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/identity/bootstrapper) topic.
