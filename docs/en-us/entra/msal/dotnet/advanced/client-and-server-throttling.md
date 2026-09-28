<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/client-and-server-throttling -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Understanding client and server throttling in MSAL.NET

## Server throttling

Microsoft Entra ID throttles applications when you call the authentication API too frequently. Most often this happens when token caching is not used because:

1. Token caching is not setup correctly \(see [Token cache serialization](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-token-cache-serialization)\).
2. Not calling [AcquireTokenSilent\(IEnumerable<String>, String\)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.clientapplicationbase.acquiretokensilent#microsoft-identity-client-clientapplicationbase-acquiretokensilent\(system-collections-generic-ienumerable\(\(system-string\)\)-system-string\)) before calling [AcquireTokenInteractive\(IEnumerable<String>\)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.ipublicclientapplication.acquiretokeninteractive#microsoft-identity-client-ipublicclientapplication-acquiretokeninteractive\(system-collections-generic-ienumerable\(\(system-string\)\)\)), [AcquireTokenByUsernamePassword\(IEnumerable<String>, String, String\)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.ipublicclientapplication.acquiretokenbyusernamepassword#microsoft-identity-client-ipublicclientapplication-acquiretokenbyusernamepassword\(system-collections-generic-ienumerable\(\(system-string\)\)-system-string-system-string\)).
3. If you are asking for a scope which does not apply to Microsoft Account \(MSA\) users, such as `User.ReadBasic.All`, resulting in cache misses.

The server signals throttling in two ways:

- For `client_credentials` grant, i.e., [AcquireTokenForClient\(IEnumerable<String>\)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.confidentialclientapplication.acquiretokenforclient#microsoft-identity-client-confidentialclientapplication-acquiretokenforclient\(system-collections-generic-ienumerable\(\(system-string\)\)\)), Microsoft Entra ID will reply with `429 Too Many Requests`, with a `Retry-After: 60` header.
- For user-facing calls, Microsoft Entra ID will send a message which results in a [MsalUiRequiredException](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.msaluirequiredexception) with an `invalid_grant` error code and a message set to `AADSTS50196: The server terminated an operation because it encountered a loop while processing a request`.

## Client throttling

MSAL detects certain conditions where the application should not make repeated calls to Microsoft Entra ID. If a call is made, then a [MsalThrottledServiceException](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.msalthrottledserviceexception) or a [MsalThrottledUiRequiredException](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.msalthrottleduirequiredexception) exception is thrown. These are subtypes of [MsalServiceException](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.msalserviceexception), so this behavior does not introduce a breaking change.

If MSAL would not apply client-side throttling the application would still not be able to acquire tokens as Microsoft Entra ID would throw the error regardless.

## Conditions to get throttled

### Microsoft Entra ID is telling the application to back off

If the server is having problems or if an application is requesting tokens too often Microsoft Entra ID will respond with `HTTP 429 (Too Many Requests)` and with `Retry-After` header, `Retry-After X seconds`. The application will see an [MsalServiceException](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.msalserviceexception) with [header details](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/exceptions/retry-policy). The throttling state is maintained for X seconds. This limit affects all flows.

The most likely culprit is that you have not setup token caching. See [Token cache serialization in MSAL.NET](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-token-cache-serialization) for details.

### Microsoft Entra ID is having problems

If Microsoft Entra ID is having problems it may respond with a `HTTP 5xx` error code with no `Retry-After` header. The throttling state is maintained for one minute. Affects only public client flows.

### Application is ignoring `MsalUiRequiredException`

MSAL throws [MsalUiRequiredException](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.msaluirequiredexception) when authentication cannot be resolved silently and the end-user needs to use a browser. This is a common occurrence when a tenant administrator introduced Multi-Factor Authentication \(MFA\) or when a user's password expires. Retrying the silent authentication cannot succeed. The throttling state is maintained for two minutes. Affects only the [AcquireTokenSilent\(IEnumerable<String>, String\)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.clientapplicationbase.acquiretokensilent#microsoft-identity-client-clientapplicationbase-acquiretokensilent\(system-collections-generic-ienumerable\(\(system-string\)\)-system-string\)) flow.
