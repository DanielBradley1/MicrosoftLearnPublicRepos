<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/migrate-confidential-client -->
<!-- Sitemap-Last-Modified: 2023-09-05 -->

# Migrate confidential client applications from ADAL.NET to MSAL.NET

In this how-to guide you'll migrate a confidential client application from Azure Active Directory Authentication Library for .NET \(ADAL.NET\) to Microsoft Authentication Library for .NET \(MSAL.NET\). Confidential client applications include web apps, web APIs, and daemon applications that call another service on their own behalf. For more information about confidential apps, see [Authentication flows and application scenarios](https://learn.microsoft.com/en-us/azure/active-directory/develop/authentication-flows-app-scenarios). If your app is based on ASP.NET Core, see [Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/).

For app registrations:

- You don't need to create a new app registration. \(You keep the same client ID.\)
- You don't need to change the preauthorizations \(admin-consented API permissions\).

## Migration steps

1. Find the code that uses ADAL.NET in your app.

   The code that uses ADAL in a confidential client app instantiates `AuthenticationContext` and calls either `AcquireTokenByAuthorizationCode` or one override of `AcquireTokenAsync` with the following parameters:

   - A `resourceId` string. This variable is the app ID URI of the web API that you want to call.
   - An instance of `IClientAssertionCertificate` or `ClientAssertion`. This instance provides the client credentials for your app to prove the identity of your app.

2. After you've identified that you have apps that are using ADAL.NET, install the MSAL.NET NuGet package [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) and update your project library references. For more information, see [Install a NuGet package](https://www.bing.com/search?q=install+nuget+package). To use token cache serializers, install [Microsoft.Identity.Web.TokenCache](https://www.nuget.org/packages/Microsoft.Identity.Web.TokenCache).
3. Update the code according to the confidential client scenario. Some steps are common and apply across all the confidential client scenarios. Other steps are unique to each scenario.

   Confidential client scenarios:

   - [Daemon scenarios](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/migrate-confidential-client?tabs=daemon#migrate-daemon-apps) supported by web apps, web APIs, and daemon console applications.
   - [Web API calling downstream web APIs](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/migrate-confidential-client?tabs=obo#migrate-a-web-api-that-calls-downstream-web-apis) supported by web APIs calling downstream web APIs on behalf of the user.
   - [Web app calling web APIs](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/migrate-confidential-client?tabs=authcode#migrate-a-web-api-that-calls-downstream-web-apis) supported by web apps that sign in users and call a downstream web API.

You might have provided a wrapper around ADAL.NET to handle certificates and caching. This guide uses the same approach to illustrate the process of migrating from ADAL.NET to MSAL.NET. However, this code is only for demonstration purposes. Don't copy/paste these wrappers or integrate them in your code as they are.

- [Daemon](#tabpanel_1_daemon)
- [Web API calling downstream web APIs](#tabpanel_1_obo)
- [Web app calling web APIs](#tabpanel_1_authcode)

### Migrate daemon apps

Daemon scenarios use the OAuth2.0 [client credential flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow). They're also called service-to-service calls. Your app acquires a token on its own behalf, not on behalf of a user.

#### Find out if your code uses daemon scenarios

The ADAL code for your app uses daemon scenarios if it contains a call to `AuthenticationContext.AcquireTokenAsync` with the following parameters:

- A resource \(app ID URI\) as a first parameter
- `IClientAssertionCertificate` or `ClientAssertion` as the second parameter

`AuthenticationContext.AcquireTokenAsync` doesn't have a parameter of type `UserAssertion`. If it does, then your app is a web API, and it uses the [web API calling downstream web APIs](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/migrate-confidential-client?tabs=obo#migrate-a-web-api-that-calls-downstream-web-apis) scenario.

#### Update the code of daemon scenarios

The following steps for updating code apply across all the confidential client scenarios:

1. Add the MSAL.NET namespace in your source code: `using Microsoft.Identity.Client;`.
2. Instead of instantiating `AuthenticationContext`, use `ConfidentialClientApplicationBuilder.Create` to instantiate `IConfidentialClientApplication`.
3. Instead of the `resourceId` string, MSAL.NET uses scopes. Because applications that use ADAL.NET are preauthorized, you can always use the following scopes: `new string[] { $"{resourceId}/.default" }`.
4. Replace the call to `AuthenticationContext.AcquireTokenAsync` with a call to `IConfidentialClientApplication.AcquireTokenXXX`, where *XXX* depends on your scenario.

In this case, replace the call to `AuthenticationContext.AcquireTokenAsync` with a call to `IConfidentialClientApplication.AcquireTokenClient`.

Here's a comparison of ADAL.NET and MSAL.NET code for daemon scenarios:

ADAL

MSAL

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Security.Cryptography.X509Certificates;
using System.Threading.Tasks;

public partial class AuthWrapper
{
const string ClientId = "Guid (AppID)";
const string authority 
= "https://login.microsoftonline.com/{tenant}";
// App ID URI of web API to call
const string resourceId = "https://target-api.domain.com";
X509Certificate2 certificate = LoadCertificate();



public async Task<AuthenticationResult> GetAuthenticationResult()
{


var authContext = new AuthenticationContext(authority);
var clientAssertionCert = new ClientAssertionCertificate(
ClientId,
certificate);


var authResult = await authContext.AcquireTokenAsync(
resourceId,
clientAssertionCert,
);

return authResult;
}
}
```

```csharp
using Microsoft.Identity.Client;
using System.Security.Cryptography.X509Certificates;
using System.Threading.Tasks;

public partial class AuthWrapper
{
const string ClientId = "Guid (Application ID)";
const string authority 
= "https://login.microsoftonline.com/{tenant}";
// App ID URI of web API to call
const string resourceId = "https://target-api.domain.com";
X509Certificate2 certificate = LoadCertificate();

IConfidentialClientApplication app;

public async Task<AuthenticationResult> GetAuthenticationResult()
{

var app = ConfidentialClientApplicationBuilder.Create(ClientId)
.WithCertificate(certificate)
.WithAuthority(authority)
.Build();

// Setup token caching https://learn.microsoft.com/azure/active-directory/develop/msal-net-token-cache-serialization?tabs=aspnet
// For example, for an in-memory cache with 1GB limit, use  
app.AddInMemoryTokenCache(services =>
{
// Configure the memory cache options
services.Configure<MemoryCacheOptions>(options =>
{
options.SizeLimit = 1024 * 1024 * 1024; // in bytes (1 GB of memory)
});
}

var authResult = await app.AcquireTokenForClient(
new [] { $"{resourceId}/.default" })
// .WithTenantId(specificTenant)
// See https://aka.ms/msal.net/withTenantId
.ExecuteAsync()
.ConfigureAwait(false);

return authResult;
}
}
```

#### Benefit from token caching

If you don't setup token caching, the token issuer will throttle you, resulting in errors. It also takes a lot less to get a token from the cache \(10-20ms\) than it is from ESTS \(500-30000ms\).

If you want to implement a distributed token cache, see [Token cache for a web app or web API \(confidential client application\)](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization?tabs=aspnet).

[Learn more about the daemon scenario](https://learn.microsoft.com/en-us/azure/active-directory/develop/scenario-daemon-overview) and how it's implemented with MSAL.NET or Microsoft.Identity.Web in new applications.

### Migrate a web API that calls downstream web APIs

Web APIs that call downstream web APIs use the OAuth2.0 [on-behalf-of \(OBO\)](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) flow. The web API uses the access token retrieved from the HTTP **Authorize** header and it validates this token. This token is then exchanged against a token to call the downstream web API. This token is used as a `UserAssertion` instance in both ADAL.NET and MSAL.NET.

#### Find out if your code uses OBO

The ADAL code for your app uses OBO if it contains a call to `AuthenticationContext.AcquireTokenAsync` with the following parameters:

- A resource \(app ID URI\) as a first parameter
- `IClientAssertionCertificate` or `ClientAssertion` as the second parameter
- A parameter of type `UserAssertion`

#### Update the code by using OBO

The following steps for updating code apply across all the confidential client scenarios:

1. Add the MSAL.NET namespace in your source code: `using Microsoft.Identity.Client;`.
2. Instead of instantiating `AuthenticationContext`, use `ConfidentialClientApplicationBuilder.Create` to instantiate `IConfidentialClientApplication`.
3. Instead of the `resourceId` string, MSAL.NET uses scopes. Because applications that use ADAL.NET are preauthorized, you can always use the following scopes: `new string[] { $"{resourceId}/.default" }`.
4. Replace the call to `AuthenticationContext.AcquireTokenAsync` with a call to `IConfidentialClientApplication.AcquireTokenXXX`, where *XXX* depends on your scenario.

In this case, we replace the call to `AuthenticationContext.AcquireTokenAsync` with a call to `IConfidentialClientApplication.AcquireTokenOnBehalfOf`.

Here's a comparison of sample OBO code for ADAL.NET and MSAL.NET:

ADAL

MSAL

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Security.Cryptography.X509Certificates;
using System.Threading.Tasks;

public partial class AuthWrapper
{
const string ClientId = "Guid (AppID)";
const string authority 
= "https://login.microsoftonline.com/common";
X509Certificate2 certificate = LoadCertificate();



public async Task<AuthenticationResult> GetAuthenticationResult(
string resourceId, 
string tokenUsedToCallTheWebApi)
{


var authContext = new AuthenticationContext(authority);
var clientAssertionCert = new ClientAssertionCertificate(
ClientId,
certificate);



var userAssertion = new UserAssertion(tokenUsedToCallTheWebApi);

var authResult = await authContext.AcquireTokenAsync(
resourceId,
clientAssertionCert,
userAssertion,
);

return authResult;
}
}
```

```csharp
using Microsoft.Identity.Client;
using System.Security.Cryptography.X509Certificates;
using System.Threading.Tasks;

public partial class AuthWrapper
{
const string ClientId = "Guid (Application ID)";
const string authority 
= "https://login.microsoftonline.com/common";
X509Certificate2 certificate = LoadCertificate();

IConfidentialClientApplication app;

public async Task<AuthenticationResult> GetAuthenticationResult(
string resourceId,
string tokenUsedToCallTheWebApi)
{

var app = ConfidentialClientApplicationBuilder.Create(ClientId)
.WithCertificate(certificate)
.WithAuthority(authority)
.Build();

// Setup token caching https://learn.microsoft.com/azure/active-directory/develop/msal-net-token-cache-serialization?tabs=aspnet
// For example, for an in-memory cache with 1GB limit. For OBO, it is recommended to use a distributed cache like Redis.
app.AddInMemoryTokenCache(services =>
{
// Configure the memory cache options
services.Configure<MemoryCacheOptions>(options =>
{
options.SizeLimit = 1024 * 1024 * 1024; // in bytes (1 GB of memory)
});
}

var userAssertion = new UserAssertion(tokenUsedToCallTheWebApi);

var authResult = await app.AcquireTokenOnBehalfOf(
new string[] { $"{resourceId}/.default" },
userAssertion)
// .WithTenantId(specificTenant) 
// See https://aka.ms/msal.net/withTenantId
.ExecuteAsync()
.ConfigureAwait(false);

return authResult;
}
}
```

#### Benefit from token caching

For token caching in OBOs, use a distributed token cache. For details, see [Token cache for a web app or web API \(confidential client app\)](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization?tabs=aspnet).

```CSharp
app.UseInMemoryTokenCaches(); // or a distributed token cache.
```

[Learn more about web APIs calling downstream web APIs](https://learn.microsoft.com/en-us/azure/active-directory/develop/scenario-web-api-call-api-overview) and how they're implemented with MSAL.NET or Microsoft.Identity.Web in new apps.

### Migrate a web app that calls web APIs

If your app uses ASP.NET Core, we strongly recommend that you update to Microsoft.Identity.Web because it processes everything for you. For a quick presentation, see the [Microsoft.Identity.Web announcement of general availability](https://github.com/AzureAD/microsoft-identity-web/wiki/1.0.0). For details about how to use it in a web app, see [Why use Microsoft.Identity.Web in web apps?](https://aka.ms/ms-id-web/webapp).

Web apps that sign in users and call web APIs on behalf of users employ the OAuth2.0 [authorization code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow). Typically:

1. The app signs in a user by executing a first leg of the authorization code flow by going to the Microsoft identity platform authorize endpoint. The user signs in and performs multi-factor authentications if needed. As an outcome of this operation, the app receives the authorization code. The authentication library isn't used at this stage.
2. The app executes the second leg of the authorization code flow. It uses the authorization code to get an access token, an ID token, and a refresh token. Your application needs to provide the `redirectUri` value, which is the URI where the Microsoft identity platform endpoint will provide the security tokens. After the app receives that URI, it typically calls `AcquireTokenByAuthorizationCode` for ADAL or MSAL to redeem the code and to get a token that will be stored in the token cache.
3. The app uses ADAL or MSAL to call `AcquireTokenSilent` to get tokens for calling the necessary web APIs from the web app controllers.

#### Find out if your code uses the auth code flow

The ADAL code for your app uses auth code flow if it contains a call to `AuthenticationContext.AcquireTokenByAuthorizationCodeAsync`.

#### Update the code by using the authorization code flow

The following steps for updating code apply across all the confidential client scenarios:

1. Add the MSAL.NET namespace in your source code: `using Microsoft.Identity.Client;`.
2. Instead of instantiating `AuthenticationContext`, use `ConfidentialClientApplicationBuilder.Create` to instantiate `IConfidentialClientApplication`.
3. Instead of the `resourceId` string, MSAL.NET uses scopes. Because applications that use ADAL.NET are preauthorized, you can always use the following scopes: `new string[] { $"{resourceId}/.default" }`.
4. Replace the call to `AuthenticationContext.AcquireTokenAsync` with a call to `IConfidentialClientApplication.AcquireTokenXXX`, where *XXX* depends on your scenario.

In this case, replace the call to `AuthenticationContext.AcquireTokenAsync` with a call to `IConfidentialClientApplication.AcquireTokenByAuthorizationCode`.

Here's a comparison of sample authorization code flows for ADAL.NET and MSAL.NET:

ADAL

MSAL

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Security.Cryptography.X509Certificates;
using System.Threading.Tasks;

public partial class AuthWrapper
{
const string ClientId = "Guid (AppID)";
const string authority 
= "https://login.microsoftonline.com/common";
private Uri redirectUri = new Uri("host/login_oidc");
X509Certificate2 certificate = LoadCertificate();



public async Task<AuthenticationResult> GetAuthenticationResult(
string resourceId,
string authorizationCode)
{


var ac = new AuthenticationContext(authority);
var clientAssertionCert = new ClientAssertionCertificate(
ClientId,
certificate);



var authResult = await ac.AcquireTokenByAuthorizationCodeAsync(
authorizationCode,
redirectUri,
clientAssertionCert,
resourceId,
);
return authResult;
}
}
```

```csharp
using Microsoft.Identity.Client;
using Microsoft.Identity.Web;
using System;
using System.Security.Claims;
using System.Security.Cryptography.X509Certificates;
using System.Threading.Tasks;

public partial class AuthWrapper
{
const string ClientId = "Guid (Application ID)";
const string authority
= "https://login.microsoftonline.com/{tenant}";
private Uri redirectUri = new Uri("host/login_oidc");
X509Certificate2 certificate = LoadCertificate();

public IConfidentialClientApplication CreateApplication()
{
IConfidentialClientApplication app;

app = ConfidentialClientApplicationBuilder.Create(ClientId)
.WithCertificate(certificate)
.WithAuthority(authority)
.WithRedirectUri(redirectUri.ToString())
.WithLegacyCacheCompatibility(false)
.Build();

// Add a token cache. For details about other serialization
// see https://aka.ms/msal-net-cca-token-cache-serialization
app.AddInMemoryTokenCache();

return app;
}

// Called from 'code received event'.
public async Task<AuthenticationResult> GetAuthenticationResult(
string resourceId,
string authorizationCode)
{
IConfidentialClientApplication app = CreateApplication();

var authResult = await app.AcquireTokenByAuthorizationCode(
new[] { $"{resourceId}/.default" },
authorizationCode)
.ExecuteAsync()
.ConfigureAwait(false);

return authResult;
}
}
```

Calling `AcquireTokenByAuthorizationCode` adds a token to the token cache when the authorization code is received. To acquire extra tokens for other resources or tenants, use `AcquireTokenSilent` in your controllers.

```csharp
public partial class AuthWrapper
{
 // Called from controllers
 public async Task<AuthenticationResult> GetAuthenticationResult(
      string resourceId2,
      string authority)
 {
  IConfidentialClientApplication app = CreateApplication();
  AuthenticationResult authResult;

  var scopes = new[] { $"{resourceId2}/.default" };
  var account = await app.GetAccountAsync(ClaimsPrincipal.Current.GetMsalAccountId());

  try
  {
   // try to get an already cached token
   authResult = await app.AcquireTokenSilent(
               scopes,
               account)
                // .WithTenantId(specificTenantId) 
                // See https://aka.ms/msal.net/withTenantId
                .ExecuteAsync().ConfigureAwait(false);
  }
  catch (MsalUiRequiredException)
  {
   // The controller will need to challenge the user
   // including asking for claims={ex.Claims}
   throw;
  }
  return authResult;
 }
}
```

#### Benefit from token caching

Because your web app uses `AcquireTokenByAuthorizationCode`, it needs to use a distributed token cache for token caching. For details, see [Token cache for a web app or web API](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization?tabs=aspnet).

```CSharp
app.UseInMemoryTokenCaches(); // or a distributed token cache.
```

#### Handling MsalUiRequiredException

When your controller attempts to acquire a token silently for different scopes/resources, MSAL.NET might throw an `MsalUiRequiredException` as expected if the user needs to re-sign-in, or if the access to the resource requires more claims \(because of a Conditional Access policy\). For details on mitigation see how to [Handle errors and exceptions in MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/exceptions/msal-error-handling).

[Learn more about web apps calling web APIs](https://learn.microsoft.com/en-us/azure/active-directory/develop/scenario-web-app-call-api-overview) and how they're implemented with MSAL.NET or Microsoft.Identity.Web in new applications.

## MSAL benefits

Key benefits of MSAL.NET for your app include:

- **Resilience**. MSAL.NET helps make your app resilient through:

  - Microsoft Entra ID Cached Credential Service \(CCS\) benefits. CCS operates as a Microsoft Entra backup.
  - Proactive renewal of tokens if the API that you call enables long-lived tokens through [continuous access evaluation](https://learn.microsoft.com/en-us/azure/active-directory/develop/app-resilience-continuous-access-evaluation).

- **Security**. You can acquire Proof of Possession \(PoP\) tokens if the web API that you want to call requires it. For details, see [Proof Of Possession tokens in MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/proof-of-possession-tokens)
- **Performance and scalability**. If you don't need to share your cache with ADAL.NET, disable the legacy cache compatibility when you're creating the confidential client application \(`.WithLegacyCacheCompatibility(false)`\) to significantly increase performance.

  ```csharp
  app = ConfidentialClientApplicationBuilder.Create(ClientId)
          .WithCertificate(certificate)
          .WithAuthority(authority)
          .WithLegacyCacheCompatibility(false)
          .Build();
  ```

## Troubleshooting

### MsalServiceException

The following troubleshooting information makes two assumptions:

- Your ADAL.NET code was working.
- You migrated to MSAL by keeping the same client ID.

If you get an exception with either of the following messages:

> `AADSTS700027: Client assertion contains an invalid signature. [Reason - The key was not found.]`

> `AADSTS90002: Tenant 'aaaabbbb-0000-cccc-1111-dddd2222eeee' not found. This may happen if there are no active` `subscriptions for the tenant. Check to make sure you have the correct tenant ID. Check with your subscription` `administrator.`

Troubleshoot the exception using these steps:

1. Confirm that you're using the latest version of [MSAL.NET](https://www.nuget.org/packages/Microsoft.Identity.Client/).
2. Confirm that the authority host that you set when building the confidential client app and the authority host that you used with ADAL are similar. In particular, is it the same [cloud](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-national-cloud) \(Azure Government, Microsoft Azure operated by 21Vianet, or Azure Germany\)?

### MsalClientException

In multi-tenant apps, specify a common authority when building the app to target a specific tenant such as, the tenant of the user when calling a web API. Since MSAL.NET 4.37.0, when you specify `.WithAzureRegion` at the app creation, you can no longer specify the Authority using `.WithAuthority` during the token requests. If you do, you'll get the following error when updating from previous versions of MSAL.NET:

`MsalClientException - "You configured WithAuthority at the request level, and also WithAzureRegion. This is not supported when the environment changes from application to request. Use WithTenantId at the request level instead."`

To remediate this issue, replace `.WithAuthority` on the AcquireTokenXXX expression by `.WithTenantId`. Specify the tenant using either a GUID or a domain name.

## Next steps

Learn more about:

- [Differences between ADAL.NET and MSAL.NET apps](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-differences-adal-net).
- [Token cache serialization in MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization)
