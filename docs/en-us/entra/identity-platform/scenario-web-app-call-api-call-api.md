<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-call-api -->
<!-- Sitemap-Last-Modified: 2025-03-21 -->

# A web app that calls web APIs: Call a web API

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Now that you have a token, you can call a protected web API. You usually call a downstream API from the controller or pages of your web app.

## Call a protected web API

Calling a protected web API depends on your language and framework of choice:

- [ASP.NET Core](#tabpanel_1_aspnetcore)
- [ASP.NET](#tabpanel_1_aspnet)
- [Java](#tabpanel_1_java)
- [Node.js](#tabpanel_1_nodejs)
- [Python](#tabpanel_1_python)

When you use *Microsoft.Identity.Web*, you have three usage options for calling an API:

- [Option 1: Call Microsoft Graph with the Microsoft Graph SDK](#option-1-call-microsoft-graph-with-the-sdk)
- [Option 2: Call a downstream web API with the helper class](#option-2-call-a-downstream-web-api-with-the-helper-class)
- [Option 3: Call a downstream web API without the helper class](#option-3-call-a-downstream-web-api-without-the-helper-class)

#### Option 1: Call Microsoft Graph with the SDK

In this scenario, you call Microsoft Graph by adding the **Microsoft.Identity.Web.GraphServiceClient** NuGet package and including `.AddMicrosoftGraph()` in *Startup.cs* as specified in [Code configuration](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-app-configuration#option-1-call-microsoft-graph). You can then directly inject the `GraphServiceClient` into your controller or page constructor to use it in the actions. The following example Razor page displays the photo of the signed-in user.

```csharp
[Authorize]
[AuthorizeForScopes(Scopes = new[] { "user.read" })]
public class IndexModel : PageModel
{
 private readonly GraphServiceClient _graphServiceClient;

 public IndexModel(GraphServiceClient graphServiceClient)
 {
    _graphServiceClient = graphServiceClient;
 }

 public async Task OnGet()
 {
  var user = await _graphServiceClient.Me.GetAsync();
  try
  {
   using (var photoStream = await _graphServiceClient.Me.Photo.Content.GetAsync())
   {
    byte[] photoByte = ((MemoryStream)photoStream).ToArray();
    ViewData["photo"] = Convert.ToBase64String(photoByte);
   }
   ViewData["name"] = user.DisplayName;
  }
  catch (Exception)
  {
   ViewData["photo"] = null;
  }
 }
}
```

For a full sample, see [ASP.NET Core web app that calls Microsoft Graph](https://github.com/Azure-Samples/active-directory-aspnetcore-webapp-openidconnect-v2/blob/master/2-WebApp-graph-user/2-1-Call-MSGraph/README.md).

#### Option 2: Call a downstream web API with the helper class

You want to call a web API other than Microsoft Graph. In that case, you add `AddDownstreamApi` in *Startup.cs* as specified in [Code configuration](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-app-configuration#option-2-call-a-downstream-web-api-other-than-microsoft-graph), and you can directly inject an `IDownstreamApi` service in your controller or page constructor and use it in the actions:

```csharp
[Authorize]
[AuthorizeForScopes(ScopeKeySection = "TodoList:Scopes")]
public class TodoListController : Controller
{
  private IDownstreamApi _downstreamApi;
  private const string ServiceName = "TodoList";

  public TodoListController(IDownstreamApi downstreamApi)
  {
    _downstreamApi = downstreamApi;
  }

  public async Task<ActionResult> Details(int id)
  {
    var value = await _downstreamApi.CallApiForUserAsync(
      ServiceName,
      options =>
      {
        options.RelativePath = $"me";
      });
      return View(value);
  }
}
```

The `CallWebApiForUserAsync` also has strongly typed generic overrides that enable you to directly receive an object. For example, the following method receives a `Todo` instance, which is a strongly typed representation of the JSON returned by the web API.

```csharp
    // GET: TodoList/Details/5
    public async Task<ActionResult> Details(int id)
    {
        var value = await _downstreamApi.CallApiForUserAsync<object, Todo>(
            ServiceName,
            null,
            options =>
            {
                options.HttpMethod = HttpMethod.Get;
                options.RelativePath = $"api/todolist/{id}";
            });
        return View(value);
    }
```

For a full sample, see [ASP.NET Core web app that calls an API](https://github.com/Azure-Samples/active-directory-aspnetcore-webapp-openidconnect-v2/tree/master/4-WebApp-your-API/4-1-MyOrg)

#### Option 3: Call a downstream web API without the helper class

You've decided to acquire a token manually using the `IAuthorizationHeaderProvider` service, and you now need to use the token. In that case, the following code continues the example code shown in [A web app that calls web APIs: Acquire a token for the app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token). The code is called in the actions of the web app controllers.

After you've acquired the token, use it as a bearer token to call the downstream API, in this case Microsoft Graph.

```csharp
public async Task<IActionResult> Profile()
{
  // Acquire the access token.
  string[] scopes = new string[]{"user.read"};
  string authorizationHeader = await IAuthorizationHeaderProvider.GetAuthorizationHeaderForUserAsync(scopes);

  // Use the access token to call a protected web API.
  HttpClient httpClient = new HttpClient();
  client.DefaultRequestHeaders.Add("Authorization", authorizationHeader);

  var response = await httpClient.GetAsync($"{webOptions.GraphApiUrl}/beta/me");

  if (response.StatusCode == HttpStatusCode.OK)
  {
    var content = await response.Content.ReadAsStringAsync();

    dynamic me = JsonConvert.DeserializeObject(content);
    ViewData["Me"] = me;
  }

  return View();
}
```

Note

You can use the same principle to call any web API.

Most Azure web APIs provide an SDK that simplifies calling the API as is the case for Microsoft Graph.

When you use *Microsoft.Identity.Web*, you have three usage options for calling an API:

- [Option 1: Call Microsoft Graph with the Microsoft Graph SDK](#option-1-call-microsoft-graph-with-the-sdk-from-owin-app)
- [Option 2: Call a downstream web API with the helper class](#option-2-call-a-downstream-web-api-with-the-helper-class-from-owin-app)
- [Option 3: Call a downstream web API without the helper class](#option-3-call-a-downstream-web-api-without-the-helper-class-from-owin-app)

#### Option 1: Call Microsoft Graph with the SDK from OWIN app

You want to call Microsoft Graph. In this scenario, you've added `AddMicrosoftGraph` in *Startup.cs* as specified in [Code configuration](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-app-configuration#option-1-call-microsoft-graph), and you can get the `GraphServiceClient` in your controller or page constructor for use in the actions by using the `GetGraphServiceClient()` extension method on the controller. The following example displays the photo of the signed-in user.

```csharp
[Authorize]
[AuthorizeForScopes(Scopes = new[] { "user.read" })]
public class HomeController : Controller
{

 public async Task GetIndex()
 {
  var graphServiceClient = this.GetGraphServiceClient();
  var user = await graphServiceClient.Me.GetAsync();
  try
  {
   using (var photoStream = await graphServiceClient.Me.Photo.Content.GetAsync())
   {
    byte[] photoByte = ((MemoryStream)photoStream).ToArray();
    ViewData["photo"] = Convert.ToBase64String(photoByte);
   }
   ViewData["name"] = user.DisplayName;
  }
  catch (Exception)
  {
   ViewData["photo"] = null;
  }
 }
}
```

For a full sample, see [ASP.NET OWIN Web app that calls Microsoft Graph](https://github.com/Azure-Samples/ms-identity-aspnet-webapp-openidconnect)

#### Option 2: Call a downstream web API with the helper class from OWIN app

You want to call a web API other than Microsoft Graph. In that case, you've added `AddDownstreamApi` in *Startup.cs* as specified in [Code configuration](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-app-configuration#option-2-call-a-downstream-web-api-other-than-microsoft-graph), and you can get `IDownstreamApi` service in your controller by calling the `GetDownstreamApi` extension method on the controller:

```csharp
[Authorize]
public class TodoListController : Controller
{ 
  public async Task<ActionResult> Details(int id)
  {
    var downstreamApi = this.GetDownstreamApi();
    var value = await downstreamApi.CallApiForUserAsync(
      ServiceName,
      options =>
      {
        options.RelativePath = $"me";
      });
      return View(value);
  }
}
```

The `CallApiForUserAsync` also has strongly typed generic overrides that enable you to directly receive an object. For example, the following method receives a `Todo` instance, which is a strongly typed representation of the JSON returned by the web API.

```csharp
    // GET: TodoList/Details/5
    public async Task<ActionResult> Details(int id)
    {
        var downstreamApi = this.GetDownstreamApi();
        var value = await downstreamApi.CallApiForUserAsync<object, Todo>(
            ServiceName,
            null,
            options =>
            {
                options.HttpMethod = HttpMethod.Get;
                options.RelativePath = $"api/todolist/{id}";
            });
        return View(value);
    }
```

#### Option 3: Call a downstream web API without the helper class from OWIN app

You've decided to acquire an authorization header using the `IAuthorizationHeaderProvider` service, and you now need to use it in your HttpClient or HttpRequest. In that case, the following code continues the example code shown in [A web app that calls web APIs: Acquire a token for the app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token). The code is called in the actions of the web app controllers.

```csharp
public async Task<IActionResult> Profile()
{
  // Acquire the access token.
  string[] scopes = new string[]{"user.read"};
  var IAuthorizationHeaderProvider = this.GetAuthorizationHeaderProvider();
  string authorizationHeader = await IAuthorizationHeaderProvider.GetAuthorizationHeaderForUserAsync(scopes);

  // Use the access token to call a protected web API.
  HttpClient httpClient = new HttpClient();
  client.DefaultRequestHeaders.Add("Authorization", authorizationHeader);

  var response = await httpClient.GetAsync($"{webOptions.GraphApiUrl}/beta/me");

  if (response.StatusCode == HttpStatusCode.OK)
  {
    var content = await response.Content.ReadAsStringAsync();

    dynamic me = JsonConvert.DeserializeObject(content);
    ViewData["Me"] = me;
  }

  return View();
}
```

```java
private String getUserInfoFromGraph(String accessToken) throws Exception {
    // Microsoft Graph user endpoint
    URL url = new URL("https://graph.microsoft.com/v1.0/me");

    HttpURLConnection conn = (HttpURLConnection) url.openConnection();

    // Set the appropriate header fields in the request header.
    conn.setRequestProperty("Authorization", "Bearer " + accessToken);
    conn.setRequestProperty("Accept", "application/json");

    String response = HttpClientHelper.getResponseStringFromConn(conn);

    int responseCode = conn.getResponseCode();
    if(responseCode != HttpURLConnection.HTTP_OK) {
        throw new IOException(response);
    }

    JSONObject responseObject = HttpClientHelper.processResponse(responseCode, response);
    return responseObject.toString();
}
```

After successfully retrieving a token, the code uses the **axios** package to query the API endpoint and retrieve a JSON result.

```js
/**
 * Attaches a given access token to a MS Graph API call
 * @param endpoint: REST API endpoint to call
 * @param accessToken: raw access token string
 */
async function fetch(endpoint, accessToken) {
    const options = {
        headers: {
            Authorization: `Bearer ${accessToken}`
        }
    };

    console.log(`request made to ${endpoint} at: ` + new Date().toString());

    try {
        const response = await axios.get(endpoint, options);
        return await response.data;
    } catch (error) {
        throw new Error(error);
    }
}
```

After successfully retrieving a token, the code uses the requests package to query the API endpoint and retrieve a JSON result.

```python
@app.route("/call_downstream_api")
def call_downstream_api():
    token = auth.get_token_for_user(app_config.SCOPE)
    if "error" in token:
        return redirect(url_for("login"))
    # Use access token to call downstream api
    api_result = requests.get(
        app_config.ENDPOINT,
        headers={'Authorization': 'Bearer ' + token['access_token']},
        timeout=30,
    ).json()
    return render_template('display.html', result=api_result)
```

## Next steps

- Learn more by building an ASP.NET Core web app that signs in users in the following multi-part [tutorial series](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-prepare-app)
- Explore Microsoft identity platform [web app samples](https://learn.microsoft.com/en-us/entra/identity-platform/sample-v2-code#web-applications)
