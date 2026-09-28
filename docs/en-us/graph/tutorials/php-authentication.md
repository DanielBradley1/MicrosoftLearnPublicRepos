<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/php-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add user authentication to PHP apps for Microsoft Graph

In this article, you add user authentication to the application you created in [Build PHP apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/php). You then use the Microsoft Graph user API to get the authenticated user.

## Add user authentication

The Microsoft Graph SDK includes authentication providers based on the [PHP League OAuth2 client](https://github.com/thephpleague/oauth2-client). However for this tutorial, you use the [device code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code) to obtain access tokens. The included authentication providers don't implement this flow, so you implement a custom access token provider.

### Create access token provider

Create a new file in the root directory of your project named **DeviceCodeTokenProvider.php**. Add the following code.

```php
<?php
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT license.

use GuzzleHttp\Client;
use Http\Promise\FulfilledPromise;
use Http\Promise\Promise;
use Http\Promise\RejectedPromise;
use Microsoft\Kiota\Abstractions\Authentication\AccessTokenProvider;
use Microsoft\Kiota\Abstractions\Authentication\AllowedHostsValidator;

class DeviceCodeTokenProvider implements AccessTokenProvider {

    private string $clientId;
    private string $tenantId;
    private string $scopes;
    private AllowedHostsValidator $allowedHostsValidator;
    private string $accessToken;
    private Client $tokenClient;

    public function __construct(string $clientId, string $tenantId, string $scopes) {
        $this->clientId = $clientId;
        $this->tenantId = $tenantId;
        $this->scopes = $scopes;
        $this->allowedHostsValidator = new AllowedHostsValidator();
        $this->allowedHostsValidator->setAllowedHosts([
            "graph.microsoft.com",
            "graph.microsoft.us",
            "dod-graph.microsoft.us",
            "graph.microsoft.de",
            "microsoftgraph.chinacloudapi.cn"
        ]);
        $this->tokenClient = new Client();
    }

    public function getAuthorizationTokenAsync(string $url, array $additionalAuthenticationContext = []): Promise {
        $parsedUrl = parse_url($url);
        $scheme = $parsedUrl["scheme"] ?? null;

        if ($scheme !== 'https' || !$this->getAllowedHostsValidator()->isUrlHostValid($url)) {
            return new FulfilledPromise(null);
        }

        // If we already have a user token, just return it
        // Tokens are valid for one hour, after that it needs to be refreshed
        if (isset($this->accessToken)) {
            return new FulfilledPromise($this->accessToken);
        }

        // https://learn.microsoft.com/azure/active-directory/develop/v2-oauth2-device-code
        $deviceCodeRequestUrl = 'https://login.microsoftonline.com/'.$this->tenantId.'/oauth2/v2.0/devicecode';
        $tokenRequestUrl = 'https://login.microsoftonline.com/'.$this->tenantId.'/oauth2/v2.0/token';

        // First POST to /devicecode
        $deviceCodeResponse = json_decode($this->tokenClient->post($deviceCodeRequestUrl, [
            'form_params' => [
                'client_id' => $this->clientId,
                'scope' => $this->scopes
            ]
        ])->getBody()->getContents());

        // Display the user prompt
        print($deviceCodeResponse->message.PHP_EOL);

        // Response also indicates how often to poll for completion
        // And gives a device code to send in the polling requests
        $interval = (int)$deviceCodeResponse->interval;
        $device_code = $deviceCodeResponse->device_code;

        // Do polling - if attempt times out the token endpoint
        // returns an error
        while (true) {
            sleep($interval);

            // POST to the /token endpoint
            $tokenResponse = $this->tokenClient->post($tokenRequestUrl, [
                'form_params' => [
                    'client_id' => $this->clientId,
                    'grant_type' => 'urn:ietf:params:oauth:grant-type:device_code',
                    'device_code' => $device_code
                ],
                // These options are needed to enable getting
                // the response body from a 4xx response
                'http_errors' => false,
                'curl' => [
                    CURLOPT_FAILONERROR => false
                ]
            ]);

            if ($tokenResponse->getStatusCode() == 200) {
                // Return the access_token
                $responseBody = json_decode($tokenResponse->getBody()->getContents());
                $this->accessToken = $responseBody->access_token;
                return new FulfilledPromise($responseBody->access_token);
            } else if ($tokenResponse->getStatusCode() == 400) {
                // Check the error in the response body
                $responseBody = json_decode($tokenResponse->getBody()->getContents());
                if (isset($responseBody->error)) {
                    $error = $responseBody->error;
                    // authorization_pending means we should keep polling
                    if (strcmp($error, 'authorization_pending') != 0) {
                        return new RejectedPromise(
                            new Exception('Token endpoint returned '.$error, 100));
                    }
                }
            }
        }
    }

    public function getAllowedHostsValidator(): AllowedHostsValidator {
        return $this->allowedHostsValidator;
    }
}
?>
```

### Configure Graph client for user authentication

Now use the `DeviceCodeTokenProvider` class to request an access token by using the [device code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code).

1. Create a new file in the root directory of your project named **GraphHelper.php**. Add the following code.

   ```php
   <?php
   class GraphHelper {
   }
   ?>
   ```

2. Add the following `using` statements inside the PHP tags.

   ```php
   use Microsoft\Graph\Generated\Models;
   use Microsoft\Graph\Generated\Users\Item\MailFolders\Item\Messages\MessagesRequestBuilderGetQueryParameters;
   use Microsoft\Graph\Generated\Users\Item\MailFolders\Item\Messages\MessagesRequestBuilderGetRequestConfiguration;
   use Microsoft\Graph\Generated\Users\Item\SendMail\SendMailPostRequestBody;
   use Microsoft\Graph\Generated\Users\Item\UserItemRequestBuilderGetQueryParameters;
   use Microsoft\Graph\Generated\Users\Item\UserItemRequestBuilderGetRequestConfiguration;
   use Microsoft\Graph\GraphRequestAdapter;
   use Microsoft\Graph\GraphServiceClient;
   use Microsoft\Kiota\Abstractions\Authentication\BaseBearerTokenAuthenticationProvider;

   require_once 'DeviceCodeTokenProvider.php';
   ```

3. Add the following code to the `GraphHelper` class.

   ```php
   private static string $clientId = '';
   private static string $tenantId = '';
   private static string $graphUserScopes = '';
   private static DeviceCodeTokenProvider $tokenProvider;
   private static GraphServiceClient $userClient;

   public static function initializeGraphForUserAuth(): void {
       GraphHelper::$clientId = $_ENV['CLIENT_ID'];
       GraphHelper::$tenantId = $_ENV['TENANT_ID'];
       GraphHelper::$graphUserScopes = $_ENV['GRAPH_USER_SCOPES'];

       GraphHelper::$tokenProvider = new DeviceCodeTokenProvider(
           GraphHelper::$clientId,
           GraphHelper::$tenantId,
           GraphHelper::$graphUserScopes);
       $authProvider = new BaseBearerTokenAuthenticationProvider(GraphHelper::$tokenProvider);
       $adapter = new GraphRequestAdapter($authProvider);
       GraphHelper::$userClient = GraphServiceClient::createWithRequestAdapter($adapter);
   }
   ```

4. Replace the empty `initializeGraph` function in **main.php** with the following.

   ```php
   function initializeGraph(): void {
       GraphHelper::initializeGraphForUserAuth();
   }
   ```

This code loads information from the .env file, and initializes two properties, a `DeviceCodeTokenProvider` object and a `GraphServiceClient` object. The `DeviceCodeTokenProvider` object is used to request an access token, and the `GraphServiceClient` object is used to make calls to Microsoft Graph.

### Test the device code flow

Next, add code to get an access token from the `GraphHelper`.

1. Add the following function to the `GraphHelper` class.

   ```php
   public static function getUserToken(): string {
       return GraphHelper::$tokenProvider
           ->getAuthorizationTokenAsync('https://graph.microsoft.com')->wait();
   }
   ```

2. Replace the empty `displayAccessToken` function in **main.php** with the following.

   ```php
   function displayAccessToken(): void {
       try {
           $token = GraphHelper::getUserToken();
           print('User token: '.$token.PHP_EOL.PHP_EOL);
       } catch (Exception $e) {
           print('Error getting access token: '.$e->getMessage().PHP_EOL.PHP_EOL);
       }
   }
   ```

3. Build and run the app. Enter `1` when prompted for an option. The application displays a URL and device code.

   ```bash
   $ php main.php

   PHP Graph Tutorial

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

1. Add the following code to the `GraphHelper` class.

   ```php
   public static function getUser(): Models\User {
       $configuration = new UserItemRequestBuilderGetRequestConfiguration();
       $configuration->queryParameters = new UserItemRequestBuilderGetQueryParameters();
       $configuration->queryParameters->select = ['displayName','mail','userPrincipalName'];
       return GraphHelper::$userClient->me()->get($configuration)->wait();
   }
   ```

2. Replace the empty `greetUser` function in **main.php** with the following.

   ```php
   function greetUser(): void {
       try {
           $user = GraphHelper::getUser();
           print('Hello, '.$user->getDisplayName().'!'.PHP_EOL);

           // For Work/school accounts, email is in Mail property
           // Personal accounts, email is in UserPrincipalName
           $email = $user->getMail();
           if (empty($email)) {
               $email = $user->getUserPrincipalName();
           }
           print('Email: '.$email.PHP_EOL.PHP_EOL);
       } catch (Exception $e) {
           print('Error getting user: '.$e->getMessage().PHP_EOL.PHP_EOL);
       }
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

The function builds a request to the [Get user](https://learn.microsoft.com/en-us/graph/api/user-get) API. This API is accessible two ways:

```http
GET /me
GET /users/{user-id}
```

In this case, the code calls the `GET /me` API endpoint. This endpoint is a shortcut method to get the authenticated user without knowing their user ID.

Note

Because the `GET /me` API endpoint gets the authenticated user, it's only available to apps that use user authentication. App-only authentication apps can't access this endpoint.

#### Requesting specific properties

The function uses the [$select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) to specify the set of properties it needs.

#### Strongly typed return type

The function returns a `User` object deserialized from the JSON response from the API. Because the code uses `$select`, only the requested properties have values in the returned `User` object. All other properties have default values.

## Next step

[Read and send email](https://learn.microsoft.com/en-us/graph/tutorials/php-email)
