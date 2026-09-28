<!-- Source: https://learn.microsoft.com/en-us/graph/sdks/customize-client -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Customize the Microsoft Graph SDK service client

The Microsoft Graph SDK client configures a default set of middleware that allows the SDK to communicate with the Microsoft Graph endpoints. This customizable default set allows you to change the client's behavior. For example, you can insert customized logging or a test handler to simulate specific scenarios. You can add and remove middleware components. It's important to note that the order in which middleware components run is significant.

- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_PHP)
- [Python](#tabpanel_1_python)
- [TypeScript](#tabpanel_1_typescript)

```csharp
// tokenCredential is one of the credential classes from Azure.Identity
// scopes is an array of permission scope strings
var authProvider = new AzureIdentityAuthenticationProvider(tokenCredential, isCaeEnabled: true, scopes: scopes);

var handlers = GraphClientFactory.CreateDefaultHandlers();

// ChaosHandler simulates random server failures
// Microsoft.Kiota.Http.HttpClientLibrary.Middleware.ChaosHandler
handlers.Add(new ChaosHandler());

var httpClient = GraphClientFactory.Create(handlers);
var customGraphClient = new GraphServiceClient(httpClient, authProvider);
```

```go
import (
    "net/http"
    "net/url"

    "github.com/Azure/azure-sdk-for-go/sdk/azcore"
    "github.com/Azure/azure-sdk-for-go/sdk/azcore/policy"
    "github.com/Azure/azure-sdk-for-go/sdk/azidentity"
    khttp "github.com/microsoft/kiota-http-go"
    graph "github.com/microsoftgraph/msgraph-sdk-go"
    graphcore "github.com/microsoftgraph/msgraph-sdk-go-core"
    "github.com/microsoftgraph/msgraph-sdk-go-core/authentication"
)
```

```go
// tokenCredential is one of the credential classes from azidentity
// scopes is an array of permission scope strings
authProvider, _ := authentication.NewAzureIdentityAuthenticationProviderWithScopes(credential, scopes)

// Get default middleware from SDK
defaultClientOptions := graph.GetDefaultClientOptions()
defaultMiddleWare := graphcore.GetDefaultMiddlewaresWithOptions(&defaultClientOptions)

// Add chaos handler to default middleware
chaosHandler := khttp.NewChaosHandler()
allMiddleware := append(defaultMiddleWare, chaosHandler)

// Create an HTTP client with the middleware
httpClient := khttp.GetDefaultClient(allMiddleware...)

// Create the adapter
// Passing nil values causes the adapter to use default implementations
adapter, _ :=
    graph.NewGraphRequestAdapterWithParseNodeFactoryAndSerializationWriterFactoryAndHttpClient(
        authProvider, nil, nil, httpClient)

graphClient := graph.NewGraphServiceClient(adapter)
```

```java
// tokenCredential is one of the credential classes from azure-identity
// scopes is a list of permission scope strings
final AzureIdentityAuthenticationProvider authProvider =
    new AzureIdentityAuthenticationProvider(credential, allowedHosts, scopes);

final ChaosHandler chaosHandler = new ChaosHandler();

final OkHttpClient httpClient = GraphClientFactory.create()
    .addInterceptor(chaosHandler).build();

if (null == httpClient) {
    throw new Exception("Could not create HTTP client.");
}

final GraphServiceClient graphClient = new GraphServiceClient(authProvider, httpClient);
```

```php
// Create the default handler stack
$handlerStack = GraphClientFactory::getDefaultHandlerStack();

// Add the chaos handler
$handlerStack->push(KiotaMiddleware::chaos());

// Create an HTTP client with the handler stack
$httpClient = GraphClientFactory::createWithMiddleware($handlerStack);

// Create the Graph service client
// $authProvider is an implementation of
// Microsoft\Kiota\Abstractions\Authentication\AuthenticationProvider
$adapter = new GraphRequestAdapter($authProvider, $httpClient);

$graphClient = GraphServiceClient::createWithRequestAdapter($adapter);
```

```python
# Create an authentication provider
# credential is one of the credential classes from azure.identity
# scopes is an array of permission scope strings
auth_provider = AzureIdentityAuthenticationProvider(credential, scopes=scopes)

# Get default middleware
# msgraph_core.GraphClientFactory
middleware = GraphClientFactory.get_default_middleware(options=None)

# Add custom middleware
# Implement a custom middleware by extending the BaseMiddleware class
# https://github.com/microsoft/kiota-http-go/blob/main/kiota_http/middleware/middleware.py
middleware.append(CustomMiddleware())

# Create an HTTP client with the middleware
http_client = GraphClientFactory.create_with_custom_middleware(middleware)

# Create a request adapter with the HTTP client
adapter = GraphRequestAdapter(auth_provider, http_client)

# Create the Graph client
graph_client = GraphServiceClient(request_adapter=adapter)
```

## Custom middleware

```python
from kiota_http.middleware.middleware import BaseMiddleware
from httpx import Request, Response, AsyncBaseTransport

# pylint: disable=too-few-public-methods
class CustomMiddleware(BaseMiddleware):
    async def send(self, request: Request, transport: AsyncBaseTransport) -> Response:
        print(request.method, request.url)
        response = await super().send(request, transport)
        return response
```

```typescript
// credential is one of the credential classes from @azure/identity
// scopes is an array of permission scope strings
const authProvider = new TokenCredentialAuthenticationProvider(credential, {
  scopes: scopes,
});

// Create an authentication handler (from @microsoft/microsoft-graph-client)
const authHandler = new AuthenticationHandler(authProvider);

// Create a chaos handler (from @microsoft/microsoft-graph-client)
const chaosHandler = new ChaosHandler();

// Create a standard HTTP handler (from @microsoft/microsoft-graph-client)
const httpHandler = new HTTPMessageHandler();

// Use setNext to chain handlers together
// auth -> chaos -> http
authHandler.setNext(chaosHandler);
chaosHandler.setNext(httpHandler);

// Pass the first middleware in the chain in the middleWare property
const graphClient = Client.initWithMiddleware({
  middleware: authHandler,
});
```

## Configuring the HTTP proxy for the client

Some environments require client applications to use an HTTP proxy before accessing the public internet. This section shows how to configure the proxy for the Microsoft Graph SDKs.

- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [PHP](#tabpanel_2_PHP)
- [Python](#tabpanel_2_python)
- [TypeScript](#tabpanel_2_typescript)

```csharp
// URI to proxy
var proxyAddress = "http://localhost:8888";

// Create an HttpClientHandler with the proxy to
// pass to the Azure.Identity token credential
var handler = new HttpClientHandler
{
    Proxy = new WebProxy(proxyAddress),
};

// Create an options object that corresponds to the
// token credential being used. For example, this sample
// uses a ClientSecretCredential, so the corresponding
// options object is ClientSecretCredentialOptions
var options = new ClientSecretCredentialOptions()
{
    Transport = new HttpClientTransport(handler),
};

var tokenCredential = new ClientSecretCredential(
    "YOUR_TENANT_ID",
    "YOUR_CLIENT_ID",
    "YOUR_CLIENT_SECRET",
    options);

// NOTE: Authentication requests will not go through the proxy.
// Azure.Identity token credential classes have their own separate method
// for configuring a proxy using TokenCredentialOptions.Transport
var authProvider = new AzureIdentityAuthenticationProvider(tokenCredential, isCaeEnabled: true, scopes: scopes);

// This example works with Microsoft.Graph 5+
// Use the GraphClientFactory to create an HttpClient with the proxy
var httpClient = GraphClientFactory.Create(proxy: new WebProxy(proxyAddress));
var graphClient = new GraphServiceClient(httpClient, authProvider);
```

```go
import (
    "net/http"
    "net/url"

    "github.com/Azure/azure-sdk-for-go/sdk/azcore"
    "github.com/Azure/azure-sdk-for-go/sdk/azcore/policy"
    "github.com/Azure/azure-sdk-for-go/sdk/azidentity"
    khttp "github.com/microsoft/kiota-http-go"
    graph "github.com/microsoftgraph/msgraph-sdk-go"
    graphcore "github.com/microsoftgraph/msgraph-sdk-go-core"
    "github.com/microsoftgraph/msgraph-sdk-go-core/authentication"
)
```

```go
proxyAddress := "http://proxy-url"
proxyUrl, _ := url.Parse(proxyAddress)

// Setup proxy for the token credential from azidentity
authClient := &http.Client{
    Transport: &http.Transport{
        Proxy: http.ProxyURL(proxyUrl),
    },
}

credential, _ := azidentity.NewClientSecretCredential(
    "CLIENT_ID", "TENANT_ID", "SECRET", &azidentity.ClientSecretCredentialOptions{
        // Pass the proxied client to the credential
        ClientOptions: policy.ClientOptions{
            Transport: authClient,
        },
    })

// scopes is an array of permission scope strings
authProvider, _ := authentication.NewAzureIdentityAuthenticationProviderWithScopes(credential, scopes)

// Get default middleware from SDK
defaultClientOptions := graph.GetDefaultClientOptions()
defaultMiddleWare := graphcore.GetDefaultMiddlewaresWithOptions(&defaultClientOptions)

// Create an HTTP client with the middleware
httpClient, _ := khttp.GetClientWithProxySettings(proxyAddress, defaultMiddleWare...)
// For authenticated proxy, use
// khttp.GetClientWithAuthenticatedProxySettings(
//     proxyAddress, "user", "password", defaultMiddleWare...)

// Create the adapter
// Passing nil values causes the adapter to use default implementations
adapter, _ :=
    graph.NewGraphRequestAdapterWithParseNodeFactoryAndSerializationWriterFactoryAndHttpClient(
        authProvider, nil, nil, httpClient)

graphClient := graph.NewGraphServiceClient(adapter)
```

```java
final String proxyHost = "localhost";
final int proxyPort = 8888;
final InetSocketAddress proxyAddress = new InetSocketAddress(proxyHost,
    proxyPort);

// Setup proxy for the token credential from azure-identity
// From the com.azure.core.http.* packages
final ProxyOptions options = new ProxyOptions(Type.HTTP, proxyAddress);
// If the proxy requires authentication, use setCredentials
options.setCredentials("username", "password");
final HttpClient authClient = new NettyAsyncHttpClientBuilder().proxy(options)
    .build();

final ClientSecretCredential credential = new ClientSecretCredentialBuilder()
    .clientId("YOUR_CLIENT_ID")
    .tenantId("YOUR_TENANT_ID")
    .clientSecret("YOUR_CLIENT_SECRET")
    .httpClient(authClient)
    .build();

if (credential == null) {
    throw new Exception("Could not create credential");
}

// scopes is a list of permission scope strings
final AzureIdentityAuthenticationProvider authProvider =
    new AzureIdentityAuthenticationProvider(credential, allowedHosts, scopes);

// Setup proxy for the Graph client
final Proxy proxy = new Proxy(Proxy.Type.HTTP, proxyAddress);

// This object is only needed if the proxy requires authentication
final Authenticator proxyAuthenticator = new Authenticator() {
    @Override
    public Request authenticate(Route route, Response response)
        throws IOException {
        String credential = Credentials.basic("username", "password");
        return response.request().newBuilder()
            .header("Proxy-Authorization", credential).build();
    }
};

// Omit proxyAuthenticator if no authentication required
final OkHttpClient httpClient = GraphClientFactory.create().proxy(proxy)
    .proxyAuthenticator(proxyAuthenticator).build();
if (null == httpClient) {
    throw new Exception("Could not create HTTP client.");
}

final GraphServiceClient graphClient = new GraphServiceClient(authProvider, httpClient);
```

```php
// Create HTTP client with a Guzzle config
// to specify proxy
$guzzleConfig = [
    'proxy' => 'http://localhost:8888'
];

$httpClient = GraphClientFactory::createWithConfig($guzzleConfig);

// Create the Graph service client
// $authProvider is an implementation of
// Microsoft\Kiota\Abstractions\Authentication\AuthenticationProvider
$adapter = new GraphRequestAdapter($authProvider, $httpClient);

$graphClient = GraphServiceClient::createWithRequestAdapter($adapter);
```

```python
# Proxy URLs
proxies = {
    'http': 'http://proxy-url',
    'https': 'http://proxy-url',
}

# Create a token credential with the proxies. It can be any
# of the credential classes from azure.identity
credential = DeviceCodeCredential(
    "client_id", tenant_id = "tenant_id", proxies = proxies)

# Create an authentication provider
# credential is one of the credential classes from azure.identity
# scopes is an array of permission scope strings
# proxies is an optional dict containing proxies configuration in requests format
auth_provider = AzureIdentityAuthenticationProvider(credential, scopes=scopes)

# HTTPX Proxy URLs
httpx_proxies = {
    'http://': proxies['http'],
    'https://': proxies['https'],
}

# Create a custom HTTP client with the proxies
# httpx.AsyncClient
# proxies is an optional dict containing proxies configuration in httpx format
http_client = AsyncClient(proxies=httpx_proxies) # type: ignore

# Apply the default Graph middleware to the HTTP client
http_client = GraphClientFactory.create_with_default_middleware(client=http_client)

# Create a request adapter with the HTTP client
adapter = GraphRequestAdapter(auth_provider, http_client)

# Create the Graph client
graph_client = GraphServiceClient(request_adapter=adapter)
```

```typescript
// Setup proxy for the token credential from @azure/identity
const credential = new ClientSecretCredential(
  'YOUR_TENANT_ID',
  'YOUR_CLIENT_ID',
  'YOUR_CLIENT_SECRET',
  {
    proxyOptions: {
      host: 'localhost',
      port: 8888,
    },
  },
);

// scopes is an array of permission scope strings
const authProvider = new TokenCredentialAuthenticationProvider(credential, {
  scopes: scopes,
});

// Create a new HTTPS proxy agent (from https-proxy-agent)
const proxyAgent = new HttpsProxyAgent('http://localhost:8888');

// Create a client with the proxy
const graphClient = Client.initWithMiddleware({
  authProvider: authProvider,
  fetchOptions: {
    agent: proxyAgent,
  },
});
```
