<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/javascript-app-only-get-users -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# List users in JavaScript apps using Microsoft Graph

In this article, you extend the application you created in [Build JavaScript apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/javascript-app-only) with Microsoft Graph user APIs. You use Microsoft Graph to list users in your organization.

1. Open **graphHelper.js** and add the following function.

   ```javascript
   export async function getUsersAsync() {
     // Ensure client isn't undefined
     if (!_appClient) {
       throw new Error('Graph has not been initialized for app-only auth');
     }

     return _appClient
       ?.api('/users')
       .select(['displayName', 'id', 'mail'])
       .top(25)
       .orderby('displayName')
       .get();
   }
   ```

2. Replace the empty `listUsersAsync` function in **index.js** with the following.

   ```javascript
   async function listUsersAsync() {
     try {
       const userPage = await getUsersAsync();
       const users = userPage.value;

       // Output each user's details
       for (const user of users) {
         console.log(`User: ${user.displayName ?? 'NO NAME'}`);
         console.log(`  ID: ${user.id}`);
         console.log(`  Email: ${user.mail ?? 'NO EMAIL'}`);
       }

       // If @odata.nextLink is not undefined, there are more users
       // available on the server
       const moreAvailable = userPage['@odata.nextLink'] != undefined;
       console.log(`\nMore users available? ${moreAvailable}`);
     } catch (err) {
       console.log(`Error getting users: ${err}`);
     }
   }
   ```

3. Run the app and choose option 2 to list users.

   ```Shell
   [1] Display access token
   [2] List users
   [3] Make a Graph call
   [0] Exit

   Select an option [1...3 / 0]: 2
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

Consider the code in the `getUsersAsync` function.

- It gets a collection of users
- It uses `select` to request specific properties
- It uses `top` to limit the number of users returned
- It uses `orderBy` to sort the response

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/javascript-app-only-extend-app)
