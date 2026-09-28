<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/python-authentication -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add user authentication to Python apps for Microsoft Graph

In this article, you add user authentication to the application you created in [Build Python apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/python). You then use the Microsoft Graph user API to get the authenticated user.

## Add user authentication

The [Azure Identity client library for Python](https://github.com/Azure/azure-sdk-for-python/tree/main/sdk/identity/azure-identity) provides many `TokenCredential` classes that implement OAuth2 token flows. The [Microsoft Graph SDK for Python \(preview\)](https://github.com/microsoftgraph/msgraph-sdk-python) uses those classes to authenticate calls to Microsoft Graph.

### Configure Graph client for user authentication

Start by using the `DeviceCodeCredential` class to request an access token by using the [device code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code).

1. Open **graph.py** and replace its entire contents with the following code.

   ```python
   from configparser import SectionProxy
   from azure.identity import DeviceCodeCredential
   from msgraph import GraphServiceClient
   from msgraph.generated.users.item.user_item_request_builder import UserItemRequestBuilder
   from msgraph.generated.users.item.mail_folders.item.messages.messages_request_builder import (
       MessagesRequestBuilder)
   from msgraph.generated.users.item.send_mail.send_mail_post_request_body import (
       SendMailPostRequestBody)
   from msgraph.generated.models.message import Message
   from msgraph.generated.models.item_body import ItemBody
   from msgraph.generated.models.body_type import BodyType
   from msgraph.generated.models.recipient import Recipient
   from msgraph.generated.models.email_address import EmailAddress

   class Graph:
       settings: SectionProxy
       device_code_credential: DeviceCodeCredential
       user_client: GraphServiceClient

       def __init__(self, config: SectionProxy):
           self.settings = config
           client_id = self.settings['clientId']
           tenant_id = self.settings['tenantId']
           graph_scopes = self.settings['graphUserScopes'].split(' ')

           self.device_code_credential = DeviceCodeCredential(client_id, tenant_id = tenant_id)
           self.user_client = GraphServiceClient(self.device_code_credential, graph_scopes)
   ```


   This code declares two private properties, a `DeviceCodeCredential` object and a `GraphServiceClient` object. The `__init__` function creates a new instance of `DeviceCodeCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `user_client`, it uses the provided credential to get an access token.

2. Add the following function to **graph.py**.

   ```python
   async def get_user_token(self):
       graph_scopes = self.settings['graphUserScopes']
       access_token = self.device_code_credential.get_token(graph_scopes)
       return access_token.token
   ```

3. Replace the empty `display_access_token` function in **main.py** with the following.

   ```python
   async def display_access_token(graph: Graph):
       token = await graph.get_user_token()
       print('User token:', token, '\n')
   ```

4. Build and run the app. Enter `1` when prompted for an option. The application displays a URL and device code.

   ```bash
   Python Graph Tutorial

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

5. Open a browser and browse to the URL displayed. Enter the provided code and sign in.

   Important

   Be mindful of any existing Microsoft 365 accounts that are logged into your browser when browsing to `https://microsoft.com/devicelogin`. Use browser features such as profiles, guest mode, or private mode to ensure that you authenticate as the account you intend to use for testing.
6. Once completed, return to the application to see the access token.

   Tip

   For validation and debugging purposes *only*, you can decode user access tokens \(for work or school accounts only\) using Microsoft's online token parser at [https://jwt.ms](https://jwt.ms). Parsing your token can be useful if you encounter token errors when calling Microsoft Graph. For example, verifying that the `scp` claim in the token contains the expected Microsoft Graph permission scopes.

## Get user

Now that authentication is configured, you can make your first Microsoft Graph API call. Add code to get the authenticated user's name and email address.

1. Add the following function to **graph.py**.

   ```python
   async def get_user(self):
       # Only request specific properties using $select
       query_params = UserItemRequestBuilder.UserItemRequestBuilderGetQueryParameters(
           select=['displayName', 'mail', 'userPrincipalName']
       )

       request_config = UserItemRequestBuilder.UserItemRequestBuilderGetRequestConfiguration(
           query_parameters=query_params
       )

       user = await self.user_client.me.get(request_configuration=request_config)
       return user
   ```

2. Replace the empty `greet_user` function in **main.py** with the following.

   ```python
   async def greet_user(graph: Graph):
       user = await graph.get_user()
       if user:
           print('Hello,', user.display_name)
           # For Work/school accounts, email is in mail property
           # Personal accounts, email is in userPrincipalName
           print('Email:', user.mail or user.user_principal_name, '\n')
   ```

If you run the app now, after you sign in the app welcomes you by name.

```bash
Hello, Megan Bowen!
Email: MeganB@contoso.com
```

### Code explained

Consider the code in the `get_user` function. It's only a few lines, but there are some key details to notice.

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

The function uses the [$select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) to specify the set of properties it needs. Microsoft Graph returns only the requested properties in the response. In `get_user`, adding `$select` is accomplished with the `select` parameter in the `MeRequestBuilderGetQueryParameters` object.

## Next step

[Read and send email](https://learn.microsoft.com/en-us/graph/tutorials/python-email)
