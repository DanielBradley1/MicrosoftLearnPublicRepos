<!-- Source: https://learn.microsoft.com/en-us/entra/msal/msal-client-applications -->
<!-- Sitemap-Last-Modified: 2024-02-09 -->

# Public client and confidential client applications

The Microsoft Authentication Library \(MSAL\) defines two types of clients - **public clients** and **confidential clients**. The two client types are distinguished by the ability to authenticate securely with the authorization server and maintain the confidentiality of client credentials.

- **Confidential client applications** are apps that run on servers, such as web apps, web API apps, or service/daemon apps. Their internals are considered difficult to access, and therefore they can keep an application secret secure and out of sight of its users. Confidential clients can hold configuration-time secrets. Each instance of the client has a distinct configuration \(including client ID and client secret\). A web app is the most common confidential client. The client ID is exposed through the web browser, but the secret is passed only through the backend and is never directly exposed.
- **Public client applications** are apps that run on consumer devices, desktop computers, or in a web browser. They're not trusted to safely keep application secrets as client applications can be reverse-engineered or inspected by their users, therefore they only access web APIs on behalf of the user. They also only support public client flows.

## Comparing the client types

The following are some similarities and differences between public and confidential client apps:

- Both types of apps maintain a user token cache and can acquire a token silently \(when the token is already in the token cache\). Confidential client apps also have an app token cache for tokens that are for the app itself. Read more about different token cache types in the [Token cache serialization](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization#token-cache-types) guide.
- Both types of apps manage user accounts and can get an account from the user token cache, get an account based on its identifier, or remove an account.

In MSAL, the client ID, also called the *application ID* or *app ID*, is used during the application initialization. It doesn't need to be passed again when the app acquires a token. This is true for both public and confidential client apps. Constructors of confidential client apps are also passed client credentials: the secret they share with the identity provider, which can be a secret key \(represented as a string\) or a certificate.

## Next steps

For more information about application configuration and instantiating, see:

- [Application configuration options](https://learn.microsoft.com/en-us/entra/identity-platform/msal-client-application-configuration)
- [Initialize client applications using MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/getting-started/initializing-client-applications)
- [Initialize client applications using MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/msal-js-initializing-client-applications)
