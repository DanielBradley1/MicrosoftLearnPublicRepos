<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/typescript-app-only-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add app-only authentication to TypeScript apps for Microsoft Graph

In this article, you add app-only authentication to the application you created in [Build TypeScript apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/typescript-app-only).

The [Azure Identity client library for JavaScript](https://www.npmjs.com/package/@azure/identity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph JavaScript client library](https://www.npmjs.com/package/@microsoft/microsoft-graph-client) uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section, you use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Open **graphHelper.ts** and add the following code.

   ```typescript
   import 'isomorphic-fetch';
   import { ClientSecretCredential } from '@azure/identity';
   import { Client, PageCollection } from '@microsoft/microsoft-graph-client';
   // prettier-ignore
   import { TokenCredentialAuthenticationProvider } from
     '@microsoft/microsoft-graph-client/authProviders/azureTokenCredentials/index.js';

   import { AppSettings } from './appSettings.js';

   let _settings: AppSettings | undefined = undefined;
   let _clientSecretCredential: ClientSecretCredential | undefined = undefined;
   let _appClient: Client | undefined = undefined;

   export function initializeGraphForAppOnlyAuth(settings: AppSettings) {
     // Ensure settings isn't null
     if (!settings) {
       throw new Error('Settings cannot be undefined');
     }

     _settings = settings;

     if (!_clientSecretCredential) {
       _clientSecretCredential = new ClientSecretCredential(
         _settings.tenantId,
         _settings.clientId,
         _settings.clientSecret,
       );
     }

     if (!_appClient) {
       const authProvider = new TokenCredentialAuthenticationProvider(
         _clientSecretCredential,
         {
           scopes: ['https://graph.microsoft.com/.default'],
         },
       );

       _appClient = Client.initWithMiddleware({
         authProvider: authProvider,
       });
     }
   }
   ```

2. Replace the empty `initializeGraph` function in **index.ts** with the following.

   ```typescript
   function initializeGraph(settings: AppSettings) {
     graphHelper.initializeGraphForAppOnlyAuth(settings);
   }
   ```

This code declares two private properties, a `ClientSecretCredential` object and a `Client` object. The `InitializeGraphForAppOnlyAuth` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `Client`. Every time an API call is made to Microsoft Graph through the `_appClient`, it uses the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to **graphHelper.ts**.

   ```typescript
   export async function getAppOnlyTokenAsync(): Promise<string> {
     // Ensure credential isn't undefined
     if (!_clientSecretCredential) {
       throw new Error('Graph has not been initialized for app-only auth');
     }

     // Request token with given scopes
     const response = await _clientSecretCredential.getToken([
       'https://graph.microsoft.com/.default',
     ]);
     return response.token;
   }
   ```

2. Replace the empty `displayAccessTokenAsync` function in **index.ts** with the following.

   ```typescript
   async function displayAccessTokenAsync() {
     try {
       const userToken = await graphHelper.getAppOnlyTokenAsync();
       console.log(`App-only token: ${userToken}`);
     } catch (err) {
       console.log(`Error getting app-only access token: ${err}`);
     }
   }
   ```

3. Run the following command in your CLI in the root of your project.

   ```bash
   npx ts-node index.ts
   ```

4. Enter `1` when prompted for an option. The application displays an access token.

   ```Shell
   TypeScript Graph App-Only Tutorial

   [1] Display access token
   [2] List users
   [3] Make a Graph call
   [0] Exit

   Select an option [1...3 / 0]: 1
   App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
   ```


   Tip


   For validation and debugging purposes *only*, you can decode app-only access tokens using Microsoft's online token parser at [https://jwt.ms](https://jwt.ms). Parsing your token can be useful if you encounter token errors when calling Microsoft Graph. For example, verifying that the `role` claim in the token contains the expected Microsoft Graph permission scopes.

## Next step

[Get users](https://learn.microsoft.com/en-us/graph/tutorials/typescript-app-only-get-users)
