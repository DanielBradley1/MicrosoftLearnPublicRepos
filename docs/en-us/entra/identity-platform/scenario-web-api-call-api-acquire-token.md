<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-acquire-token -->
<!-- Sitemap-Last-Modified: 2025-03-21 -->

# A web API that calls web APIs: Acquire a token for the app

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

After building a client application object, use it to acquire a token that you can use to call a web API.

## Code in the controller

- [ASP.NET Core](#tabpanel_1_aspnetcore)
- [ASP.NET](#tabpanel_1_aspnet)
- [Java](#tabpanel_1_java)
- [Python](#tabpanel_1_python)

*Microsoft.Identity.Web* adds extension methods that provide convenience services for calling Microsoft Graph or a downstream web API. These methods are explained in detail in [A web app that calls web APIs: Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-call-api). With these helper methods, you don't need to manually acquire a token.

If, however, you do want to manually acquire a token, the following code shows an example of using *Microsoft.Identity.Web* to do so in a home controller. It calls Microsoft Graph using the REST API \(instead of the Microsoft Graph SDK\). Usually, you don't need to get a token, you need to build an Authorization header that you add to your request. To get an authorization header, you inject the `IAuthorizationHeaderProvider` service by dependency injection in your controller's constructor \(or your page constructor if you use Blazor\), and you use it in your controller actions. This interface has methods that produce a string containing the protocol \(Bearer, Pop, ...\) and a token. To get an authorization header to call an API on behalf of the user, use \(`CreateAuthorizationHeaderForUserAsync`\). To get an authorization header to call a downstream API on behalf of the application itself, in a daemon scenario, use \(`CreateAuthorizationHeaderForAppAsync`\).

The controller methods are protected by an `[Authorize]` attribute that ensures only authenticated calls can use the web API.

```csharp
[Authorize]
public class MyApiController : Controller
{
    /// <summary>
    /// The web API will accept only tokens 1) for users, 2) that have the `access_as_user` scope for
    /// this API.
    /// </summary>
    static readonly string[] scopeRequiredByApi = new string[] { "access_as_user" };

     static readonly string[] scopesToAccessDownstreamApi = new string[] { "api://MyTodolistService/access_as_user" };

     readonly IAuthorizationHeaderProvider authorizationHeaderProvider;

    public MyApiController(IAuthorizationHeaderProvider authorizationHeaderProvider)
    {
      this.authorizationHeaderProvider = authorizationHeaderProvider;
    }

    [RequiredScopes(Scopes = scopesToAccessDownstreamApi)]
    public IActionResult Index()
    {
        // Get an authorization header.
        IAuthorizationHeaderProvider authorizationHeaderProvider = this.GetAuthorizationHeaderProvider();
        string[] scopes = new string[]{"user.read"};
        string authorizationHeader = await authorizationHeaderProvider.CreateAuthorizationHeaderForUserAsync(scopes);

        return await callTodoListService(authorizationHeader);
    }
}
```

For details about the `callTodoListService` method, see [A web API that calls web APIs: Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-call-api).

The code for ASP.NET is similar to the code shown for ASP.NET Core:

- A controller action, protected by an \[Authorize\] attribute, extracts the tenant ID and user ID of the `ClaimsPrincipal` member of the controller. \(ASP.NET uses `HttpContext.User`.\) *Microsoft.Identity.Web.OWIN* adds extension methods to the Controller that provide convenience services to call Microsoft Graph or a downstream web API, or to get an authorization header, or even a token. The methods used to call an API directly are explained in detail in [A web app that calls web APIs: Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-call-api). With these helper methods, you don't need to manually acquire a token.

If, however, you do want to manually acquire a token or build an authorization header, the following code shows how to use *Microsoft.Identity.Web* to do so in a controller. It calls an API \(Microsoft Graph\) using the REST API instead of the Microsoft Graph SDK.

To get an authorization header, you get an `IAuthorizationHeaderProvider` service from the controller using an extension method `GetAuthorizationHeaderProvider`. To get an authorization header to call an API on behalf of the user, use \(`CreateAuthorizationHeaderForUserAsync`\). To get an authorization header to call a downstream API on behalf of the application itself, in a daemon scenario, use \(`CreateAuthorizationHeaderForAppAsync`\).

The controller methods are protected by an `[Authorize]` attribute that ensures only authenticated users can use the web app.

The following snippet shows the action of the `HomeController`, which gets an authorization header to call Microsoft Graph as a REST API:

```csharp
[Authorize]
public class MyApiController : Controller
{
 [AuthorizeForScopes(Scopes = new[] { "user.read" })]
 public async Task<IActionResult> Profile()
 {
  // Get an authorization header.
  IAuthorizationHeaderProvider authorizationHeaderProvider = this.GetAuthorizationHeaderProvider();
  string[] scopes = new string[]{"user.read"};
  string authorizationHeader = await authorizationHeaderProvider.CreateAuthorizationHeaderForUserAsync(scopes);

  // Use the access token to call a protected web API.
  HttpClient client = new HttpClient();
  client.DefaultRequestHeaders.Add("Authorization", authorizationHeader);
  string json = await client.GetStringAsync(url);
 }
}
```

The following snippet shows the action of the `MyApiController`, which gets an access token to call Microsoft Graph as a REST API:

```csharp
[Authorize]
public class HomeController : Controller
{
 [AuthorizeForScopes(Scopes = new[] { "user.read" })]
 public async Task<IActionResult> Profile()
 {
  // Get an authorization header.
  ITokenAcquirer tokenAcquirer = TokenAcquirerFactory.GetDefaultInstance().GetTokenAcquirer();
  string[] scopes = new string[]{"user.read"};
  string token = await await tokenAcquirer.GetTokenForUserAsync(scopes);

  // Use the access token to call a protected web API.
  HttpClient client = new HttpClient();
  client.DefaultRequestHeaders.Add("Authorization", $"Bearer {token}");
  string json = await client.GetStringAsync(url);
 }
}
```

Here's an example of code that's called in the actions of the API controllers. It calls the downstream API - Microsoft Graph.

```java
@RestController
public class ApiController {

    @Autowired
    MsalAuthHelper msalAuthHelper;

    @RequestMapping("/graphMeApi")
    public String graphMeApi() throws MalformedURLException {

        String oboAccessToken = msalAuthHelper.getOboToken("https://graph.microsoft.com/.default");

        return callMicrosoftGraphMeEndpoint(oboAccessToken);
    }

}
```

A Python web API requires the use of middleware to validate the bearer token received from the client. The web API can then obtain the access token for a downstream API using the MSAL Python library by calling the [`acquire_token_on_behalf_of`](https://msal-python.readthedocs.io/en/latest/?badge=latest#msal.ConfidentialClientApplication.acquire_token_on_behalf_of) method.

Here's an example of code that acquires an access token using the `acquire_token_on_behalf_of` method and the Flask framework. It calls the downstream API - the Azure Management Subscriptions endpoint.

```python
def get(self):
 
        _scopes = ["https://management.azure.com/user_impersonation"]
        _azure_management_subscriptions_uri = "https://management.azure.com/subscriptions?api-version=2020-01-01"
 
        current_access_token = request.headers.get("Authorization", None)
        
        #This example only uses the default memory token cache and should not be used for production
        msal_client = msal.ConfidentialClientApplication(
                client_id=os.environ.get("CLIENT_ID"),
                authority=os.environ.get("AUTHORITY"),
                client_credential=os.environ.get("CLIENT_SECRET"))
 
        #acquire token on behalf of the user that called this API
        arm_resource_access_token = msal_client.acquire_token_on_behalf_of(
            user_assertion=current_access_token.split(' ')[1],
            scopes=_scopes
        )
 
        headers = {'Authorization': arm_resource_access_token['token_type'] + ' ' + arm_resource_access_token['access_token']}
 
        subscriptions_list = req.get(_azure_management_subscriptions_uri), headers=headers).json()
 
        return jsonify(subscriptions_list)
```

## \(Advanced\) Accessing the signed-in user's token cache from background apps, APIs, and services

You can use MSAL's token cache implementation to allow background apps, APIs, and services to use the access token cache to continue to act on behalf of users in their absence. Doing so is especially useful if the background apps and services need to continue to work on behalf of the user after the user has exited the front-end web app.

Today, most background processes use [application permissions](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#microsoft-graph-permissions) when they need to work with a user's data without them being present to authenticate or reauthenticate. Because application permissions often require admin consent, which requires elevation of privilege, unnecessary friction is encountered as the developer didn't intend to obtain permission beyond that which the user originally consented to for their app.

This code sample on GitHub shows how to avoid this unneeded friction by accessing MSAL's token cache from background apps:

[Accessing the logged-in user's token cache from background apps, APIs, and services](https://github.com/Azure-Samples/ms-identity-dotnet-advanced-token-cache)

## Next steps

Move on to the next article in this scenario, [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-call-api).
