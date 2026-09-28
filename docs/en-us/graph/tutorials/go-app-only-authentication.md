<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/go-app-only-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add app-only authentication to Go apps for Microsoft Graph

In this article, you add app-only authentication to the application you created in [Build Go apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/go-app-only).

The [Azure Identity Client Module for Go](https://github.com/Azure/azure-sdk-for-go/tree/main/sdk/azidentity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph SDK for Go](https://github.com/microsoftgraph/msgraph-sdk-go) uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section, you use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) InitializeGraphForAppAuth() error {
       clientId := os.Getenv("CLIENT_ID")
       tenantId := os.Getenv("TENANT_ID")
       clientSecret := os.Getenv("CLIENT_SECRET")
       credential, err := azidentity.NewClientSecretCredential(tenantId, clientId, clientSecret, nil)
       if err != nil {
           return err
       }

       g.clientSecretCredential = credential

       // Create an auth provider using the credential
       authProvider, err := auth.NewAzureIdentityAuthenticationProviderWithScopes(g.clientSecretCredential, []string{
           "https://graph.microsoft.com/.default",
       })
       if err != nil {
           return err
       }

       // Create a request adapter using the auth provider
       adapter, err := msgraphsdk.NewGraphRequestAdapter(authProvider)
       if err != nil {
           return err
       }

       // Create a Graph client using request adapter
       client := msgraphsdk.NewGraphServiceClient(adapter)
       g.appClient = client

       return nil
   }
   ```


   Tip


   If you're using `goimports`, some modules might be removed from your `import` statement in **graphhelper.go** on save. You might need to add the modules again to build.

2. Replace the empty `initializeGraph` function in **graphapponlytutorial.go** with the following.

   ```go
   func initializeGraph(graphHelper *graphhelper.GraphHelper) {
       err := graphHelper.InitializeGraphForAppAuth()
       if err != nil {
           log.Panicf("Error initializing Graph for app auth: %v\n", err)
       }
   }
   ```

This code initializes two properties, a `DeviceCodeCredential` object and a `GraphServiceClient` object. The `InitializeGraphForUserAuth` function creates a new instance of `DeviceCodeCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `userClient`, it uses the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) GetAppToken() (*string, error) {
       token, err := g.clientSecretCredential.GetToken(context.Background(), policy.TokenRequestOptions{
           Scopes: []string{
               "https://graph.microsoft.com/.default",
           },
       })
       if err != nil {
           return nil, err
       }

       return &token.Token, nil
   }
   ```

2. Replace the empty `displayAccessToken` function in **graphapponlytutorial.go** with the following.

   ```go
   func displayAccessToken(graphHelper *graphhelper.GraphHelper) {
       token, err := graphHelper.GetAppToken()
       if err != nil {
           log.Panicf("Error getting user token: %v\n", err)
       }

       fmt.Printf("App-only token: %s", *token)
       fmt.Println()
   }
   ```

3. Build and run the app by running `go run graphapponlytutorial`. Enter `1` when prompted for an option. The application displays an access token.

   ```bash
   Go Graph App-Only Tutorial

   Please choose one of the following options:
   0. Exit
   1. Display access token
   2. List users
   3. Make a Graph call
   1
   App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
   ```


   Tip


   For validation and debugging purposes *only*, you can decode app-only access tokens using Microsoft's online token parser at [https://jwt.ms](https://jwt.ms). Parsing your token can be useful if you encounter token errors when calling Microsoft Graph. For example, verifying that the `role` claim in the token contains the expected Microsoft Graph permission scopes.

## Next step

[Get users](https://learn.microsoft.com/en-us/graph/tutorials/go-app-only-get-users)
