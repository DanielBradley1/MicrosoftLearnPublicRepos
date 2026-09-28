<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Security considerations

The security considerations for WOPI access tokens follow.

## Preventing token trading

Some WOPI operations, such as [GetEcosystem \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getecosystem), [EnumerateAncestors \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/enumerateancestors), and [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren), return URLs that include WOPI [access tokens](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). WOPI access tokens must always be treated as per-resource, per-user by a WOPI client, and they should always expire after a period of time. WOPI deliberately doesn't define a means for a client to refresh a WOPI access token given another WOPI access token.

But WOPI is also deliberately designed to support navigation from a file or container to the [Ecosystem endpoint](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/endpoints#ecosystem-endpoint), then back to a container or file. This means that it's possible for a client to *refresh* their WOPI tokens indefinitely unless the WOPI host is careful when issuing new access tokens to mitigate the threats. We refer to this threat as *token trading*.

To illustrate the threat of token trading, consider the following scenario:

1. A WOPI client, on behalf of User A, is issued a WOPI access token, `TOKEN1`, for the file `Document.docx`. The token has a lifetime of 12 hours.
2. While `TOKEN1` is still valid, the client calls the [EnumerateAncestors \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/enumerateancestors) operation using `TOKEN1` as the access token.
3. The server responds with a URL to the parent container along with a new WOPI access token for that container, `TOKEN2`.
4. The client then calls [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren) using `TOKEN2` as the access token.
5. The server responds with the URL for the children files, including `Document.docx`, along with a new access token for `Document.docx`, `TOKEN3`.

At this point, the client has effectively traded `TOKEN1` for `TOKEN3`. If each token issued has a lifetime of 12 hours, this means a client can effectively refresh their access token for a particular file by going through the container hierarchy, without actually authenticating with the server using a non-WOPI authentication mechanism.

If unmitigated, this scenario greatly increases the potential damage caused by token leakage. If a malicious attacker gains access to `TOKEN1`, they can potentially access `Document.docx` indefinitely, as long as User A still has access to it. In other words, the attacker can impersonate User A indefinitely.

In addition, an attacker could use [EnumerateAncestors \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/enumerateancestors) and [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren) to trade `TOKEN1` for a token that's valid for any other document in the container hierarchy that the user has access to, then impersonate User A indefinitely to access those other documents and containers as well.

### Mitigation

The preferred way to mitigate this threat is to create new WOPI access tokens with the same token lifetime as the WOPI access token that was used when the operation was called. In other words, in the scenario described above, the lifetime of `TOKEN2` and `TOKEN3` should be the same as `TOKEN1`. All three tokens should expire at the same time.

This should only apply when a WOPI access token is used to create another WOPI access token. In other cases where WOPI access tokens are issued, such as from [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) or other OAuth-authenticated [Shortcut operations](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/shortcuts), or, in the case of web-based WOPI clients, by visiting a host page that issues the access token, the host-defined default access token lifetime can apply. This is safe in those cases because there's a separate primary authentication method that's also in use. In the case of [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap), it's an OAuth token. In the case of web-based WOPI clients, it's the host’s standard web authentication system.
