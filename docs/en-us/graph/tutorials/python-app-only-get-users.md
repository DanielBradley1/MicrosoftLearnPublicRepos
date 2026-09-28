<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/python-app-only-get-users -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# List users in Python apps using Microsoft Graph

In this article, you extend the application you created in [Build Python apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/python-app-only) with Microsoft Graph user APIs. You use Microsoft Graph to list users in your organization.

1. Add the following function to **graph.py**.

   ```python
   async def get_users(self):
       query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
           # Only request specific properties
           select = ['displayName', 'id', 'mail'],
           # Get at most 25 results
           top = 25,
           # Sort by display name
           orderby= ['displayName']
       )
       request_config = UsersRequestBuilder.UsersRequestBuilderGetRequestConfiguration(
           query_parameters=query_params
       )

       users = await self.app_client.users.get(request_configuration=request_config)
       return users
   ```

2. Replace the empty `list_users` function in **main.py** with the following.

   ```python
   async def list_users(graph: Graph):
       users_page = await graph.get_users()

       # Output each users's details
       if users_page and users_page.value:
           for user in users_page.value:
               print('User:', user.display_name)
               print('  ID:', user.id)
               print('  Email:', user.mail)

           # If @odata.nextLink is present
           more_available = users_page.odata_next_link is not None
           print('\nMore users available?', more_available, '\n')
   ```

3. Run the app and choose option 2 to list users.

   ```bash
   Please choose one of the following options:
   0. Exit
   1. Display access token
   2. List users
   3. Make a Graph call
   2
   User: Adele Vance
     ID: 05fb57bf-2653-4396-846d-2f210a91d9cf
     Email: AdeleV@contoso.com
   User: Alex Wilber
     ID: a36fe267-a437-4d24-b39e-7344774d606c
     Email: AlexW@contoso.com
   User: Allan Deyoung
     ID: 54cebbaa-2c56-47ec-b878-c8ff309746b0
     Email: AllanD@contoso.com
   User: Bianca Pisani
     ID: 9a7dcbd0-72f0-48a9-a9fa-03cd46641d49
     Email: None
   User: Brian Johnson (TAILSPIN)
     ID: a8989e40-be57-4c2e-bf0b-7cdc471e9cc4
     Email: BrianJ@contoso.com

   ...

   More users available? True
   ```

## Code explained

Consider the code in the `get_users` function.

- It gets a collection of users
- It uses `$select` to request specific properties
- It uses `$top` to limit the number of users returned
- It uses `$orderBy` to sort the response

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/python-app-only-extend-app)
