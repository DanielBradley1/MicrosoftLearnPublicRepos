<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/identity/sessioncontext -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Optional Session Context String

A Session Context String may be returned from the authentication process. Microsoft 365 for mobile will pass this string in an HTTP header in calls to the token endpoint URL \([**RFC 6749#section-3.2**](https://tools.ietf.org/html/rfc6749.html#section-3.2)\) and authenticated calls to the bootstrapper \([GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getnewaccesstoken), [Shortcut operations](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/shortcuts)\).

The Session Context String is optional, and for the storage provider's use. A possible scenario would be to include a hint about a “tenant” so endpoints can know where they need to fetch and/or validate tokens.

Returning a Session Context string is done via an `sc=` URL parameter appended to the value of the [Location](https://tools.ietf.org/html/rfc7231#section-7.1.2) header from the [302 Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.3) response at the end of the sign-in flow.

Important

The contents of the `sc=` parameter must be URL encoded.

For example, to return the following information:

- Redirection URI is `https://localhost`
- Authorization code \([**RFC 6749#section-4.1.2**](https://tools.ietf.org/html/rfc6749.html#section-4.1.2)\) is “abcdefg”
- Session Context String is “hello:World”

The [Location](https://tools.ietf.org/html/rfc7231#section-7.1.2) header in the [302 Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.3) response would be:

`Location: https://localhost/?code=abcdefg&sc=hello%3AWorld`

If present, the session context string will be included as an HTTP header when calls are made to the token exchange endpoint, and OAuth2 authenticated calls to the bootstrapper \([GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getnewaccesstoken), [Shortcut operations](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/shortcuts)\) as follows:

`X-WOPI-SessionContext: hello:World`
