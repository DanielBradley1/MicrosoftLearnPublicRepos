<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/python-app-only-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add app-only authentication to Python apps for Microsoft Graph

In this article, you add app-only authentication to the application you created in [Build Python apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/python-app-only).

The [Azure Identity client library for Python](https://github.com/Azure/azure-sdk-for-python/tree/main/sdk/identity/azure-identity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph SDK for Python \(preview\)](https://github.com/microsoftgraph/msgraph-sdk-python) uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section, you use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Open **graph.py** and replace its entire contents with the following code.

   ```python
   from configparser import SectionProxy
   from azure.identity.aio import ClientSecretCredential
   from msgraph import GraphServiceClient
   from msgraph.generated.users.users_request_builder import UsersRequestBuilder

   class Graph:
       settings: SectionProxy
       client_credential: ClientSecretCredential
       app_client: GraphServiceClient

       def __init__(self, config: SectionProxy):
           self.settings = config
           client_id = self.settings['clientId']
           tenant_id = self.settings['tenantId']
           client_secret = self.settings['clientSecret']

           self.client_credential = ClientSecretCredential(tenant_id, client_id, client_secret)
           self.app_client = GraphServiceClient(self.client_credential) # type: ignore
   ```


   This code declares two private properties, an `ClientSecretCredential` object and a `GraphServiceClient` object. The `__init__` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `app_client`, it uses the provided credential to get an access token.

2. Add the following function to **graph.py**.

   ```python
   async def get_app_only_token(self):
       graph_scope = 'https://graph.microsoft.com/.default'
       access_token = await self.client_credential.get_token(graph_scope)
       return access_token.token
   ```

3. Replace the empty `display_access_token` function in **main.py** with the following.

   ```python
   async def display_access_token(graph: Graph):
       token = await graph.get_app_only_token()
       print('App-only token:', token, '\n')
   ```

4. Build and run the app. Enter `1` when prompted for an option. The application displays an access token.

   ```bash
   Python Graph App-Only Tutorial

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

[Get users](https://learn.microsoft.com/en-us/graph/tutorials/python-app-only-get-users)
