<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add app-only authentication to .NET apps for Microsoft Graph

In this article, you add app-only authentication to the application you created in [Build .NET apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only).

The [Azure Identity client library for .NET](https://www.nuget.org/packages/Azure.Identity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph .NET client library](https://github.com/microsoftgraph/msgraph-sdk-dotnet) uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section, you use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Create a new file in the **GraphTutorial** directory named **GraphHelper.cs** and add the following code to that file.

   ```csharp
   using Azure.Core;
   using Azure.Identity;
   using Microsoft.Graph;
   using Microsoft.Graph.Models;

   class GraphHelper
   {
   }
   ```

2. Add the following code to the `GraphHelper` class.

   ```csharp
   // Settings object
   private static Settings? settings;

   // App-ony auth token credential
   private static ClientSecretCredential? clientSecretCredential;

   // Client configured with app-only authentication
   private static GraphServiceClient? appClient;

   public static void InitializeGraphForAppOnlyAuth(Settings settings)
   {
       GraphHelper.settings = settings;

       // Ensure settings isn't null
       _ = settings ??
           throw new NullReferenceException("Settings cannot be null");

       GraphHelper.settings = settings;

       clientSecretCredential ??= new ClientSecretCredential(
               GraphHelper.settings.TenantId, GraphHelper.settings.ClientId, GraphHelper.settings.ClientSecret);

       appClient ??= new GraphServiceClient(
               clientSecretCredential,
               /* Use the default scope, which will request the scopes
                  configured on the app registration */
               ["https://graph.microsoft.com/.default"]);
   }
   ```

3. Replace the empty `InitializeGraph` function in **Program.cs** with the following.

   ```csharp
   void InitializeGraph(Settings settings)
   {
       GraphHelper.InitializeGraphForAppOnlyAuth(settings);
   }
   ```

This code declares two private properties, a `ClientSecretCredential` object and a `GraphServiceClient` object. The `InitializeGraphForAppOnlyAuth` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `_appClient`, it uses the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to the `GraphHelper` class.

   ```csharp
   public static async Task<string> GetAppOnlyTokenAsync()
   {
       // Ensure credential isn't null
       _ = clientSecretCredential ??
           throw new NullReferenceException("Graph has not been initialized for app-only auth");

       // Request token with given scopes
       var context = new TokenRequestContext(["https://graph.microsoft.com/.default"]);
       var response = await clientSecretCredential.GetTokenAsync(context);
       return response.Token;
   }
   ```

2. Replace the empty `DisplayAccessTokenAsync` function in **Program.cs** with the following.

   ```csharp
   async Task DisplayAccessTokenAsync()
   {
       try
       {
           var appOnlyToken = await GraphHelper.GetAppOnlyTokenAsync();
           Console.WriteLine($"App-only token: {appOnlyToken}");
       }
       catch (Exception ex)
       {
           Console.WriteLine($"Error getting app-only access token: {ex.Message}");
       }
   }
   ```

3. Build and run the app. Enter `1` when prompted for an option. The application displays an access token.

   ```Shell
   .NET Graph Tutorial

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

[Get users](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only-get-users)
