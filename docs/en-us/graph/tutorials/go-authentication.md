<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/go-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add user authentication to Go apps for Microsoft Graph

In this article, you add user authentication to the application you created in [Build Go apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/go). You then use the Microsoft Graph user API to get the authenticated user.

## Add user authentication

The [Azure Identity Client Module for Go](https://github.com/Azure/azure-sdk-for-go/tree/main/sdk/azidentity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph SDK for Go](https://github.com/microsoftgraph/msgraph-sdk-go) uses those classes to authenticate calls to Microsoft Graph.

### Configure Graph client for user authentication

Start by using the `DeviceCodeCredential` class to request an access token by using the [device code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code).

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) InitializeGraphForUserAuth() error {
       clientId := os.Getenv("CLIENT_ID")
       tenantId := os.Getenv("TENANT_ID")
       scopes := os.Getenv("GRAPH_USER_SCOPES")
       g.graphUserScopes = strings.Split(scopes, ",")

       // Create the device code credential
       credential, err := azidentity.NewDeviceCodeCredential(&azidentity.DeviceCodeCredentialOptions{
           ClientID: clientId,
           TenantID: tenantId,
           UserPrompt: func(ctx context.Context, message azidentity.DeviceCodeMessage) error {
               fmt.Println(message.Message)
               return nil
           },
       })
       if err != nil {
           return err
       }

       g.deviceCodeCredential = credential

       // Create an auth provider using the credential
       authProvider, err := auth.NewAzureIdentityAuthenticationProviderWithScopes(credential, g.graphUserScopes)
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
       g.userClient = client

       return nil
   }
   ```


   Tip


   If you're using `goimports`, some modules might be removed from your `import` statement in **graphhelper.go** on save. You might need to add the modules again to build.

2. Replace the empty `initializeGraph` function in **graphtutorial.go** with the following.

   ```go
   func initializeGraph(graphHelper *graphhelper.GraphHelper) {
       err := graphHelper.InitializeGraphForUserAuth()
       if err != nil {
           log.Panicf("Error initializing Graph for user auth: %v\n", err)
       }
   }
   ```

This code initializes two properties, a `DeviceCodeCredential` object and a `GraphServiceClient` object. The `InitializeGraphForUserAuth` function creates a new instance of `DeviceCodeCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `userClient`, it uses the provided credential to get an access token.

### Test the DeviceCodeCredential

Next, add code to get an access token from the `DeviceCodeCredential`.

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) GetUserToken() (*string, error) {
       token, err := g.deviceCodeCredential.GetToken(context.Background(), policy.TokenRequestOptions{
           Scopes: g.graphUserScopes,
       })
       if err != nil {
           return nil, err
       }

       return &token.Token, nil
   }
   ```

2. Replace the empty `displayAccessToken` function in **graphtutorial.go** with the following.

   ```go
   func displayAccessToken(graphHelper *graphhelper.GraphHelper) {
       token, err := graphHelper.GetUserToken()
       if err != nil {
           log.Panicf("Error getting user token: %v\n", err)
       }

       fmt.Printf("User token: %s", *token)
       fmt.Println()
   }
   ```

3. Build and run the app by running `go run graphtutorial`. Enter `1` when prompted for an option. The application displays a URL and device code.

   ```bash
   Go Graph Tutorial

   Please choose one of the following options:
   0. Exit
   1. Display access token
   2. List my inbox
   3. Send mail
   4. Make a Graph call
   1
   To sign in, use a web browser to open the page https://microsoft.com/devicelogin and
   enter the code RB2RUD56D to authenticate.
   ```

4. Open a browser and browse to the URL displayed. Enter the provided code and sign in.

   Important

   Be mindful of any existing Microsoft 365 accounts that are logged into your browser when browsing to `https://microsoft.com/devicelogin`. Use browser features such as profiles, guest mode, or private mode to ensure that you authenticate as the account you intend to use for testing.
5. Once completed, return to the application to see the access token.

   Tip

   For validation and debugging purposes *only*, you can decode user access tokens \(for work or school accounts only\) using Microsoft's online token parser at [https://jwt.ms](https://jwt.ms). Parsing your token can be useful if you encounter token errors when calling Microsoft Graph. For example, verifying that the `scp` claim in the token contains the expected Microsoft Graph permission scopes.

## Get user

Now that authentication is configured, you can make your first Microsoft Graph API call. Add code to get the authenticated user's name and email address.

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) GetUser() (models.Userable, error) {
       query := users.UserItemRequestBuilderGetQueryParameters{
           // Only request specific properties
           Select: []string{"displayName", "mail", "userPrincipalName"},
       }

       return g.userClient.Me().Get(context.Background(),
           &users.UserItemRequestBuilderGetRequestConfiguration{
               QueryParameters: &query,
           })
   }
   ```

2. Replace the empty `greetUser` function in **graphtutorial.go** with the following.

   ```go
   func greetUser(graphHelper *graphhelper.GraphHelper) {
       user, err := graphHelper.GetUser()
       if err != nil {
           log.Panicf("Error getting user: %v\n", err)
       }

       fmt.Printf("Hello, %s!\n", *user.GetDisplayName())

       // For Work/school accounts, email is in Mail property
       // Personal accounts, email is in UserPrincipalName
       email := user.GetMail()
       if email == nil {
           email = user.GetUserPrincipalName()
       }

       fmt.Printf("Email: %s\n", *email)
       fmt.Println()
   }
   ```

If you run the app now, after you sign in the app welcomes you by name.

```bash
Hello, Megan Bowen!
Email: MeganB@contoso.com
```

### Code explained

Consider the code in the `getUser` function. It's only a few lines, but there are some key details to notice.

#### Accessing 'me'

The function uses the `userClient.Me` request builder, which builds a request to the [Get user](https://learn.microsoft.com/en-us/graph/api/user-get) API. This API is accessible two ways:

```http
GET /me
GET /users/{user-id}
```

In this case, the code calls the `GET /me` API endpoint. This endpoint is a shortcut method to get the authenticated user without knowing their user ID.

Note

Because the `GET /me` API endpoint gets the authenticated user, it's only available to apps that use user authentication. App-only authentication apps can't access this endpoint.

#### Requesting specific properties

The function uses the `Select` property in the request's query parameters to specify the set of properties it needs. This property adds the [$select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) to the API call.

#### Strongly typed return type

The function returns a `Userable` object deserialized from the JSON response from the API. Because the code uses `Select`, only the requested properties have values in the returned `Userable` object. All other properties have default values.

## Next step

[Read and send email](https://learn.microsoft.com/en-us/graph/tutorials/go-email)
