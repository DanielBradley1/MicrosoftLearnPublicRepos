<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/java-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add user authentication to Java apps for Microsoft Graph

In this article, you add user authentication to the application you created in [Build Java apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/java). You then use the Microsoft Graph user API to get the authenticated user.

## Add user authentication

The [Azure Identity client library for Java](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/identity/azure-identity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph SDK for Java](https://github.com/microsoftgraph/msgraph-sdk-java) uses those classes to authenticate calls to Microsoft Graph.

### Configure Graph client for user authentication

Start by using the `DeviceCodeCredential` class to request an access token by using the [device code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code).

1. Create a new file in the **./app/src/main/java/graphtutorial** directory named **Graph.java** and add the following code to that file.

   ```java
   package graphtutorial;

   import java.util.List;
   import java.util.Properties;
   import java.util.function.Consumer;

   import com.azure.core.credential.AccessToken;
   import com.azure.core.credential.TokenRequestContext;
   import com.azure.identity.DeviceCodeCredential;
   import com.azure.identity.DeviceCodeCredentialBuilder;
   import com.azure.identity.DeviceCodeInfo;
   import com.microsoft.graph.models.BodyType;
   import com.microsoft.graph.models.EmailAddress;
   import com.microsoft.graph.models.ItemBody;
   import com.microsoft.graph.models.Message;
   import com.microsoft.graph.models.MessageCollectionResponse;
   import com.microsoft.graph.models.Recipient;
   import com.microsoft.graph.models.User;
   import com.microsoft.graph.serviceclient.GraphServiceClient;
   import com.microsoft.graph.users.item.sendmail.SendMailPostRequestBody;
   ```

2. Add an empty **Graph** class definition.

   ```java
   public class Graph {
   }
   ```

3. Add the following code to the `Graph` class.

   ```java
   private static Properties _properties;
   private static DeviceCodeCredential _deviceCodeCredential;
   private static GraphServiceClient _userClient;

   public static void initializeGraphForUserAuth(Properties properties, Consumer<DeviceCodeInfo> challenge) throws Exception {
       // Ensure properties isn't null
       if (properties == null) {
           throw new Exception("Properties cannot be null");
       }

       _properties = properties;

       final String clientId = properties.getProperty("app.clientId");
       final String tenantId = properties.getProperty("app.tenantId");
       final String[] graphUserScopes = properties.getProperty("app.graphUserScopes").split(",");

       _deviceCodeCredential = new DeviceCodeCredentialBuilder()
           .clientId(clientId)
           .tenantId(tenantId)
           .challengeConsumer(challenge)
           .build();

       _userClient = new GraphServiceClient(_deviceCodeCredential, graphUserScopes);
   }
   ```

4. Replace the empty `initializeGraph` function in **App.java** with the following.

   ```java
   private static void initializeGraph(Properties properties) {
       try {
           Graph.initializeGraphForUserAuth(properties,
               challenge -> System.out.println(challenge.getMessage()));
       } catch (Exception e)
       {
           System.out.println("Error initializing Graph for user auth");
           System.out.println(e.getMessage());
       }
   }
   ```

This code declares two private properties, a `DeviceCodeCredential` object and a `GraphServiceClient` object. The `InitializeGraphForUserAuth` function creates a new instance of `DeviceCodeCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `_userClient`, it uses the provided credential to get an access token.

### Test the DeviceCodeCredential

Next, add code to get an access token from the `DeviceCodeCredential`.

1. Add the following function to the `Graph` class.

   ```java
   public static String getUserToken() throws Exception {
       // Ensure credential isn't null
       if (_deviceCodeCredential == null) {
           throw new Exception("Graph has not been initialized for user auth");
       }

       final String[] graphUserScopes = _properties.getProperty("app.graphUserScopes").split(",");

       final TokenRequestContext context = new TokenRequestContext();
       context.addScopes(graphUserScopes);

       final AccessToken token = _deviceCodeCredential.getTokenSync(context);
       return token.getToken();
   }
   ```

2. Replace the empty `displayAccessToken` function in **App.java** with the following.

   ```java
   private static void displayAccessToken() {
       try {
           final String accessToken = Graph.getUserToken();
           System.out.println("Access token: " + accessToken);
       } catch (Exception e) {
           System.out.println("Error getting access token");
           System.out.println(e.getMessage());
       }
   }
   ```

3. Build and run the app. Enter `1` when prompted for an option. The application displays a URL and device code.

   ```bash
   Java Graph Tutorial

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

1. Open **Graph.java** and add the following function to the `Graph` class.

   ```java
   public static User getUser() throws Exception {
       // Ensure client isn't null
       if (_userClient == null) {
           throw new Exception("Graph has not been initialized for user auth");
       }

       return _userClient.me().get(requestConfig -> {
           requestConfig.queryParameters.select = new String[] {"displayName", "mail", "userPrincipalName"};
       });
   }
   ```

2. Replace the empty `greetUser` function in **App.java** with the following.

   ```java
   private static void greetUser() {
       try {
           final User user = Graph.getUser();
           // For Work/school accounts, email is in mail property
           // Personal accounts, email is in userPrincipalName
           final String email = user.getMail() == null ? user.getUserPrincipalName() : user.getMail();
           System.out.println("Hello, " + user.getDisplayName() + "!");
           System.out.println("Email: " + email);
       } catch (Exception e) {
           System.out.println("Error getting user");
           System.out.println(e.getMessage());
       }
   }
   ```

If you run the app now, after you sign in the app welcomes you by name.

```bash
Hello, Megan Bowen!
Email: MeganB@contoso.com
```

### Code explained

Consider the code in the `greetUser` function. It's only a few lines, but there are some key details to notice.

#### Accessing 'me'

The function uses the `_userClient.me` request builder, which builds a request to the [Get user](https://learn.microsoft.com/en-us/graph/api/user-get) API. This API is accessible two ways:

```http
GET /me
GET /users/{user-id}
```

In this case, the code calls the `GET /me` API endpoint. This endpoint is a shortcut method to get the authenticated user without knowing their user ID.

Note

Because the `GET /me` API endpoint gets the authenticated user, it's only available to apps that use user authentication. App-only authentication apps can't access this endpoint.

#### Requesting specific properties

The function uses the `select` property on the request configuration to specify the set of properties it needs. This property adds the [$select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) to the API call.

#### Strongly typed return type

The function returns a `com.microsoft.graph.models.User` object deserialized from the JSON response from the API. Because the code uses `select`, only the requested properties have values in the returned `User` object. All other properties have default values.

## Next step

[Read and send email](https://learn.microsoft.com/en-us/graph/tutorials/java-email)
