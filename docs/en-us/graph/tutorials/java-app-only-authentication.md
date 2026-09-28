<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/java-app-only-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add app-only authentication to Java apps for Microsoft Graph

In this article, you add app-only authentication to the application you created in [Build Java apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/java-app-only).

The [Azure Identity client library for Java](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/identity/azure-identity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph SDK for Java](https://github.com/microsoftgraph/msgraph-sdk-java) uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section, you use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Create a new file in the **./app/src/main/java/graphapponlytutorial** directory named **Graph.java** and add the following code to that file.

   ```java
   package graphapponlytutorial;

   import java.util.Properties;

   import com.azure.core.credential.AccessToken;
   import com.azure.core.credential.TokenRequestContext;
   import com.azure.identity.ClientSecretCredential;
   import com.azure.identity.ClientSecretCredentialBuilder;
   import com.microsoft.graph.models.UserCollectionResponse;
   import com.microsoft.graph.serviceclient.GraphServiceClient;
   ```

2. Add an empty **Graph** class definition.

   ```java
   public class Graph {
   }
   ```

3. Add the following code to the `Graph` class.

   ```java
   private static Properties _properties;
   private static ClientSecretCredential _clientSecretCredential;
   private static GraphServiceClient _appClient;

   public static void initializeGraphForAppOnlyAuth(Properties properties) throws Exception {
       // Ensure properties isn't null
       if (properties == null) {
           throw new Exception("Properties cannot be null");
       }

       _properties = properties;

       if (_clientSecretCredential == null) {
           final String clientId = _properties.getProperty("app.clientId");
           final String tenantId = _properties.getProperty("app.tenantId");
           final String clientSecret = _properties.getProperty("app.clientSecret");

           _clientSecretCredential = new ClientSecretCredentialBuilder()
               .clientId(clientId)
               .tenantId(tenantId)
               .clientSecret(clientSecret)
               .build();
       }

       if (_appClient == null) {
           _appClient = new GraphServiceClient(_clientSecretCredential,
                   new String[] { "https://graph.microsoft.com/.default" });
       }
   }
   ```

4. Replace the empty `initializeGraph` function in **App.java** with the following.

   ```java
   private static void initializeGraph(Properties properties) {
       try {
           Graph.initializeGraphForAppOnlyAuth(properties);
       } catch (Exception e)
       {
           System.out.println("Error initializing Graph for user auth");
           System.out.println(e.getMessage());
       }
   }
   ```

This code declares two private properties, a `ClientSecretCredential` object and a `GraphServiceClient` object. The `initializeGraphForAppOnlyAuth` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `_appClient`, it uses the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to the `Graph` class.

   ```java
   public static String getAppOnlyToken() throws Exception {
       // Ensure credential isn't null
       if (_clientSecretCredential == null) {
           throw new Exception("Graph has not been initialized for app-only auth");
       }

       // Request the .default scope as required by app-only auth
       final String[] graphScopes = new String[] {"https://graph.microsoft.com/.default"};

       final TokenRequestContext context = new TokenRequestContext();
       context.addScopes(graphScopes);

       final AccessToken token = _clientSecretCredential.getToken(context).block();
       return token.getToken();
   }
   ```

2. Replace the empty `displayAccessToken` function in **App.java** with the following.

   ```java
   private static void displayAccessToken() {
       try {
           final String accessToken = Graph.getAppOnlyToken();
           System.out.println("Access token: " + accessToken);
       } catch (Exception e) {
           System.out.println("Error getting access token");
           System.out.println(e.getMessage());
       }
   }
   ```

3. Build and run the app. Enter `1` when prompted for an option. The application displays an access token.

   ```bash
   Java App-Only Graph Tutorial

   Please choose one of the following options:
   0. Exit
   1. Display access token
   2. List users
   3. Make a Graph call
   1
   App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
   ```


   Tip


   For validation and debugging purposes *only*, you can decode user access tokens \(for work or school accounts only\) using Microsoft's online token parser at [https://jwt.ms](https://jwt.ms). Parsing your token can be useful if you encounter token errors when calling Microsoft Graph. For example, verifying that the `scp` claim in the token contains the expected Microsoft Graph permission scopes.

## Next step

[Get users](https://learn.microsoft.com/en-us/graph/tutorials/java-app-only-get-users)
