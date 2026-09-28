<!-- Source: https://learn.microsoft.com/en-us/graph/sdks/use-beta -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Use the Microsoft Graph SDKs with the beta API

Many Microsoft Graph SDKs use the [v1.0](https://learn.microsoft.com/en-us/graph/api/overview?view=graph-rest-1.0&preserve-view=false) Microsoft Graph endpoint by default. The SDKs can be used with the [beta](https://learn.microsoft.com/en-us/graph/api/overview?view=graph-rest-beta&preserve-view=true) endpoint for nonproduction applications. The method for accessing the beta endpoint depends on your SDK.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)
- [TypeScript](#tabpanel_1_typescript)

To call the API, you must install the [Microsoft.Graph.Beta](https://www.nuget.org/packages/Microsoft.Graph.Beta) package. Usage is the same as the `Microsoft.Graph` package.

```csharp
// Version 5.x
using Microsoft.Graph.Beta;
// Version 4.x and earlier
// using Microsoft.Graph;

// Create a new instance of GraphServiceClient.
GraphServiceClient graphClient = new GraphServiceClient(...);
```

To call the API, you must install the [Microsoft Graph Beta SDK for Go](https://github.com/microsoftgraph/msgraph-beta-sdk-go) package.

```go
import (
    graphbeta "github.com/microsoftgraph/msgraph-beta-sdk-go"
)
client := graphbeta.NewGraphServiceClientWithCredentials(credentials, scopes)
```

To call the API, you must install the [Microsoft Graph Beta Java SDK](https://github.com/microsoftgraph/msgraph-beta-sdk-java). Usage is the same as the nonbeta SDK.

```Java
GraphServiceClient graphClient = new GraphServiceClient(tokenCredential, scopes);
```

The [Microsoft Graph Beta SDK for PHP](https://github.com/microsoftgraph/msgraph-beta-sdk-php) supports the beta endpoint and models. Use the SDK for the beta endpoint in the same way as the SDK for the v1 endpoint.

To use the [Microsoft Graph Beta SDK for Python](https://github.com/microsoftgraph/msgraph-beta-sdk-python), install the SDK for the beta endpoint with the following command:

```py
pip install msgraph-beta-sdk
```

Use the SDK for the beta endpoint in the same way as the SDK for the v1 endpoint.

The [Microsoft Graph JavaScript Client Library](https://github.com/microsoftgraph/msgraph-sdk-javascript) can call the beta API in one of two ways.

- You can set the version on the `MicrosoftGraph.Client` when you create it. All requests made by the client go to the specified version.

  ```typescript
  const clientOptions: ClientOptions = {
    defaultVersion: 'beta',
    ...
  };

  // Initialize Graph client
  const client = MicrosoftGraph.Client.initWithMiddleware(clientOptions);
  ```

- You can set the version on a specific request by using the `version` function on the `GraphRequest` object.

  ```typescript
  const user = await client
    .api('/me')
    .version('beta')
    .get();
  ```

## Related content

[SDKs in preview or GA status](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview#sdks-in-preview-or-ga-status).
