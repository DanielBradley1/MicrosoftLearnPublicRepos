<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only-get-users -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# List users in .NET apps using Microsoft Graph

In this article, you extend the application you created in [Build .NET apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only) with Microsoft Graph user APIs. You use Microsoft Graph to list users in your organization.

1. Open **./GraphHelper.cs** and add the following function to the **GraphHelper** class.

   ```csharp
   public static Task<UserCollectionResponse?> GetUsersAsync()
   {
       // Ensure client isn't null
       _ = appClient ??
           throw new NullReferenceException("Graph has not been initialized for app-only auth");

       return appClient.Users.GetAsync((config) =>
       {
           /* Only request specific properties */
           config.QueryParameters.Select = ["displayName", "id", "mail"];
           /* Get at most 25 results */
           config.QueryParameters.Top = 25;
           /* Sort by display name */
           config.QueryParameters.Orderby = ["displayName"];
       });
   }
   ```

2. Replace the empty `ListUsersAsync` function in **Program.cs** with the following.

   ```csharp
   async Task ListUsersAsync()
   {
       try
       {
           var userPage = await GraphHelper.GetUsersAsync();

           if (userPage?.Value == null)
           {
               Console.WriteLine("No results returned.");
               return;
           }

           // Output each users's details
           foreach (var user in userPage.Value)
           {
               Console.WriteLine($"User: {user.DisplayName ?? "NO NAME"}");
               Console.WriteLine($"  ID: {user.Id}");
               Console.WriteLine($"  Email: {user.Mail ?? "NO EMAIL"}");
           }

           // If NextPageRequest is not null, there are more users
           // available on the server
           // Access the next page like:
           // var nextPageRequest = new UsersRequestBuilder(userPage.OdataNextLink, _appClient.RequestAdapter);
           // var nextPage = await nextPageRequest.GetAsync();
           var moreAvailable = !string.IsNullOrEmpty(userPage.OdataNextLink);

           Console.WriteLine($"\nMore users available? {moreAvailable}");
       }
       catch (Exception ex)
       {
           Console.WriteLine($"Error getting users: {ex.Message}");
       }
   }
   ```

3. Run the app and choose option 2 to list users.

   ```Shell
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
     Email: NO EMAIL
   User: Brian Johnson (TAILSPIN)
     ID: a8989e40-be57-4c2e-bf0b-7cdc471e9cc4
     Email: BrianJ@contoso.com

   ...

   More users available? True
   ```

## Code explained

Consider the code in the `GetUsersAsync` function.

- It gets a collection of users
- It uses `Select` to request specific properties
- It uses `Top` to limit the number of users returned
- It uses `OrderBy` to sort the response

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only-extend-app)
