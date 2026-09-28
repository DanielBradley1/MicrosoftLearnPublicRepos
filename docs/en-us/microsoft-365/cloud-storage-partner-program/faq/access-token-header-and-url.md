<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/access-token-header-and-url -->
<!-- Sitemap-Last-Modified: 2022-06-02 -->

# Why does Office for the web pass the access token in both the Authorization HTTP header and as a URL parameter?

Office for the web passes the WOPI [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) both as a URL parameter \(called `access_token`\) and in the [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) header. This applies to all WOPI requests that originate from Office for the web.

This is done primarily for compatibility reasons. Some host rely on the [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) header because they are using an OAuth stack for creating and managing WOPI access tokens. Because WOPI does not define a way for a host to indicate that they are using OAuth, Office for the web passes the access token both ways for maximum compatibility.

Tip

As a best practice, WOPI hosts should use the access token value from the URL parameter. This is the preferred way to pass access tokens, and not all WOPI clients will pass it in the [**Authorization**](https://tools.ietf.org/html/rfc7235#section-4.2) header.
