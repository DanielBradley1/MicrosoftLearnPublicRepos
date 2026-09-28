<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/dotnet-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add user authentication to .NET apps for Microsoft Graph

In this article, you add user authentication to the application you created in [Build .NET apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/dotnet). You then use the Microsoft Graph user API to get the authenticated user.

## Add user authentication

The [Azure Identity client library for .NET](https://www.nuget.org/packages/Azure.Identity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph .NET client library](https://github.com/microsoftgraph/msgraph-sdk-dotnet) uses those classes to authenticate calls to Microsoft Graph.

### Configure Graph client for user authentication

Start by using the `DeviceCodeCredential` class to request an access token by using the [device code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code).

1. Create a new file in the **GraphTutorial** directory named **GraphHelper.cs** and add the following code to that file.

   ```csharp
   using Azure.Core;
   using Azure.Identity;
   using Microsoft.Graph;
   using Microsoft.Graph.Models;
   using Microsoft.Graph.Me.SendMail;

   class GraphHelper
   {
   }
   ```

2. Add the following code to the `GraphHelper` class.

   ```csharp
   // Settings object
   private static Settings? settings;

   // User auth token credential
   private static DeviceCodeCredential? deviceCodeCredential;

   // Client configured with user authentication
   private static GraphServiceClient? userClient;

   public static void InitializeGraphForUserAuth(
       Settings settings,
       Func<DeviceCodeInfo, CancellationToken, Task> deviceCodePrompt)
   {
       GraphHelper.settings = settings;

       var options = new DeviceCodeCredentialOptions
       {
           ClientId = settings.ClientId,
           TenantId = settings.TenantId,
           DeviceCodeCallback = deviceCodePrompt,
       };

       deviceCodeCredential = new DeviceCodeCredential(options);

       userClient = new GraphServiceClient(deviceCodeCredential, settings.GraphUserScopes);
   }
   ```

3. Replace the empty `InitializeGraph` function in **Program.cs** with the following.

   ```csharp
   void InitializeGraph(Settings settings)
   {
       GraphHelper.InitializeGraphForUserAuth(
           settings,
           (info, cancel) =>
           {
               // Display the device code message to
               // the user. This tells them
               // where to go to sign in and provides the
               // code to use.
               Console.WriteLine(info.Message);
               return Task.FromResult(0);
           });
   }
   ```

This code declares two private properties, a `DeviceCodeCredential` object and a `GraphServiceClient` object. The `InitializeGraphForUserAuth` function creates a new instance of `DeviceCodeCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `_userClient`, it uses the provided credential to get an access token.

### Test the DeviceCodeCredential

Next, add code to get an access token from the `DeviceCodeCredential`.

1. Add the following function to the `GraphHelper` class.

   ```csharp
   public static async Task<string> GetUserTokenAsync()
   {
       // Ensure credential isn't null
       _ = deviceCodeCredential ??
           throw new NullReferenceException("Graph has not been initialized for user auth");

       // Ensure scopes isn't null
       _ = settings?.GraphUserScopes ?? throw new ArgumentNullException("Argument 'scopes' cannot be null");

       // Request token with given scopes
       var context = new TokenRequestContext(settings.GraphUserScopes);
       var response = await deviceCodeCredential.GetTokenAsync(context);
       return response.Token;
   }
   ```

2. Replace the empty `DisplayAccessTokenAsync` function in **Program.cs** with the following.

   ```csharp
   async Task DisplayAccessTokenAsync()
   {
       try
       {
           var userToken = await GraphHelper.GetUserTokenAsync();
           Console.WriteLine($"User token: {userToken}");
       }
       catch (Exception ex)
       {
           Console.WriteLine($"Error getting user access token: {ex.Message}");
       }
   }
   ```

3. Build and run the app. Enter `1` when prompted for an option. The application displays a URL and device code.

   ```Shell
   .NET Graph Tutorial

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

1. Open **./GraphHelper.cs** and add the following function to the **GraphHelper** class.

   ```csharp
   public static Task<User?> GetUserAsync()
   {
       // Ensure client isn't null
       _ = userClient ??
           throw new NullReferenceException("Graph has not been initialized for user auth");

       return userClient.Me.GetAsync((config) =>
       {
           // Only request specific properties
           config.QueryParameters.Select = ["displayName", "mail", "userPrincipalName"];
       });
   }
   ```

2. Replace the empty `GreetUserAsync` function in **Program.cs** with the following.

   ```csharp
   async Task GreetUserAsync()
   {
       try
       {
           var user = await GraphHelper.GetUserAsync();
           Console.WriteLine($"Hello, {user?.DisplayName}!");

           // For Work/school accounts, email is in Mail property
           // Personal accounts, email is in UserPrincipalName
           Console.WriteLine($"Email: {user?.Mail ?? user?.UserPrincipalName ?? string.Empty}");
       }
       catch (Exception ex)
       {
           Console.WriteLine($"Error getting user: {ex.Message}");
       }
   }
   ```

If you run the app now, after you sign in the app welcomes you by name.

```Shell
Hello, Megan Bowen!
Email: MeganB@contoso.com
```

### Code explained

Consider the code in the `GetUserAsync` function. It's only a few lines, but there are some key details to notice.

#### Accessing 'me'

The function uses the `_userClient.Me` request builder, which builds a request to the [Get user](https://learn.microsoft.com/en-us/graph/api/user-get) API. This API is accessible two ways:

```http
GET /me
GET /users/{user-id}
```

In this case, the code calls the `GET /me` API endpoint. This endpoint is a shortcut method to get the authenticated user without knowing their user ID.

Note

Because the `GET /me` API endpoint gets the authenticated user, it's only available to apps that use user authentication. App-only authentication apps can't access this endpoint.

#### Requesting specific properties

The function uses the `Select` method on the request to specify the set of properties it needs. This method adds the [$select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) to the API call.

#### Strongly typed return type

The function returns a `Microsoft.Graph.User` object deserialized from the JSON response from the API. Because the code uses `Select`, only the requested properties have values in the returned `User` object. All other properties have default values.

## Next step

[Read and send email](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-email)
