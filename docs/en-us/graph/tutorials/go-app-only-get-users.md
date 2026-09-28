<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/go-app-only-get-users -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# List users in Go apps using Microsoft Graph

In this article, you extend the application you created in [Build Go apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/go-app-only) with Microsoft Graph user APIs. You use Microsoft Graph to list users in your organization.

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) GetUsers() (models.UserCollectionResponseable, error) {
       var topValue int32 = 25
       query := users.UsersRequestBuilderGetQueryParameters{
           // Only request specific properties
           Select: []string{"displayName", "id", "mail"},
           // Get at most 25 results
           Top: &topValue,
           // Sort by display name
           Orderby: []string{"displayName"},
       }

       return g.appClient.Users().
           Get(context.Background(),
               &users.UsersRequestBuilderGetRequestConfiguration{
                   QueryParameters: &query,
               })
   }
   ```

2. Replace the empty `listUsers` function in **graphapponlytutorial.go** with the following.

   ```go
   func listUsers(graphHelper *graphhelper.GraphHelper) {
       users, err := graphHelper.GetUsers()
       if err != nil {
           log.Panicf("Error getting users: %v", err)
       }

       // Output each user's details
       for _, user := range users.GetValue() {
           fmt.Printf("User: %s\n", *user.GetDisplayName())
           fmt.Printf("  ID: %s\n", *user.GetId())

           noEmail := "NO EMAIL"
           email := user.GetMail()
           if email == nil {
               email = &noEmail
           }
           fmt.Printf("  Email: %s\n", *email)
       }

       // If GetOdataNextLink does not return nil,
       // there are more users available on the server
       nextLink := users.GetOdataNextLink()

       fmt.Println()
       fmt.Printf("More users available? %t\n", nextLink != nil)
       fmt.Println()
   }
   ```

3. Run the app, sign in, and choose option 2 to list users.

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

   More users available? true
   ```

## Code explained

Consider the code in the `GetUsers` function.

- It gets a collection of users
- It uses `Select` to request specific properties
- It uses `Top` to limit the number of users returned
- It uses `OrderBy` to sort the response

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/go-app-only-extend-app)
