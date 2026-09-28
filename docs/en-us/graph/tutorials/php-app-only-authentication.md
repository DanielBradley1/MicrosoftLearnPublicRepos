<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/php-app-only-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add app-only authentication to PHP apps for Microsoft Graph

In this article, you add app-only authentication to the application you created in [Build PHP apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/php-app-only).

## Configure Graph client for app-only authentication

In this section, you use the `PhpLeagueAuthenticationProvider` class to request an access token by using the [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Create a new file in the root directory of your project named **GraphHelper.php**. Add the following code.

   ```php
   <?php
   class GraphHelper {
   }
   ?>
   ```

2. Add the following `using` statements inside the PHP tags.

   ```php
   use Microsoft\Graph\Core\Authentication\GraphPhpLeagueAccessTokenProvider;
   use Microsoft\Graph\Generated\Models;
   use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetQueryParameters;
   use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;
   use Microsoft\Graph\GraphServiceClient;
   use Microsoft\Kiota\Authentication\Oauth\ClientCredentialContext;
   ```

3. Add the following code to the `GraphHelper` class.

   ```php
   private static string $clientId = '';
   private static string $clientSecret = '';
   private static string $tenantId = '';
   private static ClientCredentialContext $tokenContext;
   private static GraphServiceClient $appClient;

   public static function initializeGraphForAppOnlyAuth(): void {
       GraphHelper::$clientId = $_ENV['CLIENT_ID'];
       GraphHelper::$clientSecret = $_ENV['CLIENT_SECRET'];
       GraphHelper::$tenantId = $_ENV['TENANT_ID'];

       GraphHelper::$tokenContext = new ClientCredentialContext(
           GraphHelper::$tenantId,
           GraphHelper::$clientId,
           GraphHelper::$clientSecret);

       GraphHelper::$appClient = new GraphServiceClient(
           GraphHelper::$tokenContext, ['https://graph.microsoft.com/.default']);
   }
   ```

4. Replace the empty `initializeGraph` function in **main.php** with the following.

   ```php
   function initializeGraph(): void {
       GraphHelper::initializeGraphForAppOnlyAuth();
   }
   ```

This code loads information from the .env file, and initializes two properties, a `ClientCredentialContext` object and a `GraphServiceClient` object. The `ClientCredentialContext` object is used to authenticate requests, and the `GraphServiceClient` object is used to make calls to Microsoft Graph.

## Test the client credentials flow

Next, add code to get an access token from the `GraphHelper`.

1. Add the following function to the `GraphHelper` class.

   ```php
   public static function getAppOnlyToken(): string {
       // Create an access token provider to get the token
       $tokenProvider = new GraphPhpLeagueAccessTokenProvider(GraphHelper::$tokenContext);
       return $tokenProvider
           ->getAuthorizationTokenAsync('https://graph.microsoft.com')
           ->wait();
   }
   ```

2. Replace the empty `displayAccessToken` function in **main.php** with the following.

   ```php
   function displayAccessToken(): void {
       try {
           $token = GraphHelper::getAppOnlyToken();
           print('App-only token: '.$token.PHP_EOL.PHP_EOL);
       } catch (Exception $e) {
           print('Error getting access token: '.$e->getMessage().PHP_EOL.PHP_EOL);
       }
   }
   ```

3. Build and run the app. Enter `1` when prompted for an option. The application displays the access token it fetched using the authentication information configured previously in the environment variables.

   ```bash
   $ php main.php

   PHP Graph Tutorial

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

[Get users](https://learn.microsoft.com/en-us/graph/tutorials/php-app-only-get-users)
