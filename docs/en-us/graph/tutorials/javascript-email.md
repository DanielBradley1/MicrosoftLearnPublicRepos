<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/javascript-email -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add email capabilities to JavaScript apps using Microsoft Graph

In this article, you extend the application you created in [Build JavaScript apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/javascript) with Microsoft Graph mail APIs. You use Microsoft Graph to list the user's inbox and send an email.

## List user's inbox

Start by listing messages in the user's email inbox.

1. Open **graphHelper.js** and add the following function.

   ```javascript
   export async function getInboxAsync() {
     // Ensure client isn't undefined
     if (!_userClient) {
       throw new Error('Graph has not been initialized for user auth');
     }

     return _userClient
       .api('/me/mailFolders/inbox/messages')
       .select(['from', 'isRead', 'receivedDateTime', 'subject'])
       .top(25)
       .orderby('receivedDateTime DESC')
       .get();
   }
   ```

2. Replace the empty `ListInboxAsync` function in **index.js** with the following.

   ```javascript
   async function listInboxAsync() {
     try {
       const messagePage = await getInboxAsync();
       const messages = messagePage.value;

       // Output each message's details
       for (const message of messages) {
         console.log(`Message: ${message.subject ?? 'NO SUBJECT'}`);
         console.log(`  From: ${message.from?.emailAddress?.name ?? 'UNKNOWN'}`);
         console.log(`  Status: ${message.isRead ? 'Read' : 'Unread'}`);
         console.log(`  Received: ${message.receivedDateTime}`);
       }

       // If @odata.nextLink is not undefined, there are more messages
       // available on the server
       const moreAvailable = messagePage['@odata.nextLink'] != undefined;
       console.log(`\nMore messages available? ${moreAvailable}`);
     } catch (err) {
       console.log(`Error getting user's inbox: ${err}`);
     }
   }
   ```

3. Run the app, sign in, and choose option 2 to list your inbox.

   ```bash
   [1] Display access token
   [2] List my inbox
   [3] Send mail
   [4] Make a Graph call
   [0] Exit

   Select an option [1...4 / 0]: 2
   Message: Updates from Ask HR and other communities
     From: Contoso Demo on Yammer
     Status: Read
     Received: 12/30/2021 4:54:54 AM -05:00
   Message: Employee Initiative Thoughts
     From: Patti Fernandez
     Status: Read
     Received: 12/28/2021 5:01:10 PM -05:00
   Message: Voice Mail (11 seconds)
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021 5:00:46 PM -05:00
   Message: Our Spring Blog Update
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021 4:49:46 PM -05:00
   Message: Atlanta Flight Reservation
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021 4:35:42 PM -05:00
   Message: Atlanta Trip Itinerary - down time
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021 4:22:04 PM -05:00

   ...

   More messages available? true
   ```

### getInboxAsync explained

Consider the code in the `getInboxAsync` function.

#### Accessing well-known mail folders

The function passes `/me/mailFolders/inbox/messages` to the `_userClient.api` request builder, which builds a request to the [List messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages) API. Because it includes the `/mailFolders/inbox` portion of the API endpoint, the API only returns messages in the requested mail folder. In this case, because the inbox is a default, well-known folder inside a user's mailbox, it's accessible via its well-known name. Nondefault folders are accessed the same way, by replacing the well-known name with the mail folder's ID property. For details on the available well-known folder names, see [mailFolder resource type](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder).

#### Accessing a collection

Unlike the `getUserAsync` function from the previous section, which returns a single object, this method returns a collection of messages. Most APIs in Microsoft Graph that return a collection don't return all available results in a single response. Instead, they use [paging](https://learn.microsoft.com/en-us/graph/paging) to return a portion of the results while providing a method for clients to request the next page.

##### Default page sizes

APIs that use paging implement a default page size. For messages, the default value is 10. Clients can request more \(or less\) by using the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top-parameter) query parameter. In `getInboxAsync`, adding `$top` is accomplished with the `.top(25)` method.

Note

The value passed to `.top()` is an upper-bound, not an explicit number. The API returns a number of messages *up to* the specified value.

##### Getting subsequent pages

If there are more results available on the server, collection responses include an `@odata.nextLink` property with an API URL to access the next page. The JavaScript client library exposes this property on `PageCollection` objects. If this property isn't undefined, there are more results available.

The value of `@odata.nextLink` can be passed to `_userClient.api` to get the next page of results. Alternatively, you can use the `PageIterator` object from the client library to [iterate over all available pages](https://learn.microsoft.com/en-us/graph/sdks/paging).

#### Sorting collections

The function uses the `orderby` method on the request to request results sorted by the time the message is received \(`receivedDateTime` property\). It includes the `DESC` keyword so that messages received more recently are listed first. This method adds the [$orderby query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#orderby-parameter) to the API call.

## Send mail

Now add the ability to send an email message as the authenticated user.

1. Open **graphHelper.js** and add the following function.

   ```javascript
   export async function sendMailAsync(subject, body, recipient) {
     // Ensure client isn't undefined
     if (!_userClient) {
       throw new Error('Graph has not been initialized for user auth');
     }

     // Create a new message
     const message = {
       subject: subject,
       body: {
         content: body,
         contentType: 'text',
       },
       toRecipients: [
         {
           emailAddress: {
             address: recipient,
           },
         },
       ],
     };

     // Send the message
     return _userClient.api('me/sendMail').post({
       message: message,
     });
   }
   ```

2. Replace the empty `sendMailAsync` function in **index.js** with the following.

   ```javascript
   async function sendMailToSelfAsync() {
     try {
       // Send mail to the signed-in user
       // Get the user for their email address
       const user = await getUserAsync();
       const userEmail = user?.mail ?? user?.userPrincipalName;

       if (!userEmail) {
         console.log("Couldn't get your email address, canceling...");
         return;
       }

       await sendMailAsync('Testing Microsoft Graph', 'Hello world!', userEmail);
       console.log('Mail sent.');
     } catch (err) {
       console.log(`Error sending mail: ${err}`);
     }
   }
   ```

3. Run the app, sign in, and choose option 3 to send an email to yourself.

   ```Shell
   [1] Display access token
   [2] List my inbox
   [3] Send mail
   [4] Make a Graph call
   [0] Exit

   Select an option [1...4 / 0]: 3
   Mail sent.
   ```


   Note


   If you're testing with a developer tenant from the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program), the email you send might not be delivered, and you might receive a nondelivery report. If you want to unblock sending mail from your tenant, contact support via the [Microsoft 365 admin center](https://admin.microsoft.com/).

4. To verify the message was received, choose option 2 to list your inbox.

### sendMailAsync explained

Consider the code in the `sendMailAsync` function.

#### Sending mail

The function passes `/me/sendMail` to the `_userClient.api` request builder, which builds a request to the [Send mail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) API. The request builder takes a `Message` object representing the message to send.

#### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To create items with the client library, you create an instance of the class representing the data \(in this case, `Message`\), set the desired properties, then send it in the API call. Because the call is sending data, the `post` method is used instead of `get`.

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/javascript-extend-app)
