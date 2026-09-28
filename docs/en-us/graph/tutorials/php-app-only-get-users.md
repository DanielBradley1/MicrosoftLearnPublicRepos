<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/php-app-only-get-users -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# List users in PHP apps using Microsoft Graph

In this article, you extend the application you created in [Build PHP apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/php-app-only) with Microsoft Graph user APIs. You use Microsoft Graph to list users in your organization.

1. Add the following code to the `GraphHelper` class.

   ```php
   public static function getUsers(): Models\UserCollectionResponse {
       $configuration = new UsersRequestBuilderGetRequestConfiguration();
       $configuration->queryParameters = new UsersRequestBuilderGetQueryParameters();
       // Only request specific properties
       $configuration->queryParameters->select = ['displayName','id','mail'];
       // Sort by display name
       $configuration->queryParameters->orderby = ['displayName'];
       // Get at most 25 results
       $configuration->queryParameters->top = 25;

       return GraphHelper::$appClient->users()->get($configuration)->wait();
   }
   ```

2. Replace the empty `listUsers` function in **main.php** with the following.

   ```php
   function listUsers(): void {
       try {
           $users = GraphHelper::getUsers();

           // Output each user's details
           foreach ($users->getValue() as $user) {
               print('User: '.$user->getDisplayName().PHP_EOL);
               print('  ID: '.$user->getId().PHP_EOL);
               $email = $user->getMail();
               $email = isset($email) ? $email : 'NO EMAIL';
               print('  Email: '.$email.PHP_EOL);
           }

           $nextLink = $users->getOdataNextLink();
           $moreAvailable = isset($nextLink) && $nextLink != '' ? 'True' : 'False';
           print(PHP_EOL.'More users available? '.$moreAvailable.PHP_EOL.PHP_EOL);
       } catch (Exception $e) {
           print(PHP_EOL.'Error getting users: '.$e->getMessage().PHP_EOL.PHP_EOL);
       }
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

Consider the code in the `getUsers` function.

- It gets a collection of users.
- It uses `queryParameters->select` to request specific properties
- It uses `queryParameters->top` to limit the number of users returned
- It uses `queryParameters->orderby` to sort the response

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/php-app-only-extend-app)
