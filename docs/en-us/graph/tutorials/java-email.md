<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/java-email -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add email capabilities to Java apps using Microsoft Graph

s

In this article, you extend the application you created in [Build Java apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/java) with Microsoft Graph mail APIs. You use Microsoft Graph to list the user's inbox and send an email.

## List user's inbox

Start by listing messages in the user's email inbox.

1. Open **Graph.java** and add the following function to the `Graph` class.

   ```java
   public static MessageCollectionResponse getInbox() throws Exception {
       // Ensure client isn't null
       if (_userClient == null) {
           throw new Exception("Graph has not been initialized for user auth");
       }

       return _userClient.me()
           .mailFolders()
           .byMailFolderId("inbox")
           .messages()
           .get(requestConfig -> {
               requestConfig.queryParameters.select = new String[] { "from", "isRead", "receivedDateTime", "subject" };
               requestConfig.queryParameters.top = 25;
               requestConfig.queryParameters.orderby = new String[] { "receivedDateTime DESC" };
           });
   }
   ```

2. Replace the empty `listInbox` function in **App.java** with the following.

   ```java
   private static void listInbox() {
       try {
           final MessageCollectionResponse messages = Graph.getInbox();

           // Output each message's details
           for (Message message: messages.getValue()) {
               System.out.println("Message: " + message.getSubject());
               System.out.println("  From: " + message.getFrom().getEmailAddress().getName());
               System.out.println("  Status: " + (message.getIsRead() ? "Read" : "Unread"));
               System.out.println("  Received: " + message.getReceivedDateTime()
                   // Values are returned in UTC, convert to local time zone
                   .atZoneSameInstant(ZoneId.systemDefault()).toLocalDateTime()
                   .format(DateTimeFormatter.ofLocalizedDateTime(FormatStyle.SHORT)));
           }

           final Boolean moreMessagesAvailable = messages.getOdataNextLink() != null;
           System.out.println("\nMore messages available? " + moreMessagesAvailable);
       } catch (Exception e) {
           System.out.println("Error getting inbox");
           System.out.println(e.getMessage());
       }
   }
   ```

3. Run the app, sign in, and choose option 2 to list your inbox.

   ```bash
   Please choose one of the following options:
   0. Exit
   1. Display access token
   2. List my inbox
   3. Send mail
   4. Make a Graph call
   2
   Message: Updates from Ask HR and other communities
     From: Contoso Demo on Yammer
     Status: Read
     Received: 12/30/2021, 4:54:54 AM
   Message: Employee Initiative Thoughts
     From: Patti Fernandez
     Status: Read
     Received: 12/28/2021, 5:01:10 PM
   Message: Voice Mail (11 seconds)
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021, 5:00:46 PM
   Message: Our Spring Blog Update
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021, 4:49:46 PM
   Message: Atlanta Flight Reservation
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021, 4:35:42 PM
   Message: Atlanta Trip Itinerary - down time
     From: Alex Wilber
     Status: Unread
     Received: 12/28/2021, 4:22:04 PM

   ...

   More messages available? true
   ```

### getInbox explained

Consider the code in the `getInbox` function.

#### Accessing well-known mail folders

The function uses the `_userClient.me().mailFolders().byMailFolderId("inbox").messages()` request builder, which builds a request to the [List messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages) API. Because it includes the `byMailFolderId("inbox")` request builder, the API only returns messages in the requested mail folder. In this case, because the inbox is a default, well-known folder inside a user's mailbox, it's accessible via its well-known name. Nondefault folders are accessed the same way, by replacing the well-known name with the mail folder's ID property. For details on the available well-known folder names, see [mailFolder resource type](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder).

#### Accessing a collection

Unlike the `getUser` function from the previous section, which returns a single object, this method returns a collection of messages. Most APIs in Microsoft Graph that return a collection don't return all available results in a single response. Instead, they use [paging](https://learn.microsoft.com/en-us/graph/paging) to return a portion of the results while providing a method for clients to request the next page.

##### Default page sizes

APIs that use paging implement a default page size. For messages, the default value is 10. Clients can request more \(or less\) by using the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top-parameter) query parameter. In `getInbox`, adding `$top` is accomplished with the `top` property in the request configuration.

Note

The value set in `top` is an upper-bound, not an explicit number. The API returns a number of messages *up to* the specified value.

##### Getting subsequent pages

If there are more results available on the server, collection responses include an `@odata.nextLink` property with an API URL to access the next page. The Java client library provides the `getOdataNextLink` method on collection response objects. If this method returns non-null, there are more results available.

#### Sorting collections

The function uses the `orderBy` property on the request configuration to request results sorted by the time the message is received \(`receivedDateTime` property\). It includes the `DESC` keyword so that messages received more recently are listed first. This property adds the [$orderby query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#orderby-parameter) to the API call.

## Send mail

Now add the ability to send an email message as the authenticated user.

1. Open **Graph.java** and add the following function to the `Graph` class.

   ```java
   public static void sendMail(String subject, String body, String recipient) throws Exception {
       // Ensure client isn't null
       if (_userClient == null) {
           throw new Exception("Graph has not been initialized for user auth");
       }

       // Create a new message
       final Message message = new Message();
       message.setSubject(subject);
       final ItemBody itemBody = new ItemBody();
       itemBody.setContent(body);
       itemBody.setContentType(BodyType.Text);
       message.setBody(itemBody);

       final EmailAddress emailAddress = new EmailAddress();
       emailAddress.setAddress(recipient);
       final Recipient toRecipient = new Recipient();
       toRecipient.setEmailAddress(emailAddress);
       message.setToRecipients(List.of(toRecipient));

       final SendMailPostRequestBody postRequest = new SendMailPostRequestBody();
       postRequest.setMessage(message);

       // Send the message
       _userClient.me()
           .sendMail()
           .post(postRequest);
   }
   ```

2. Replace the empty `sendMail` function in **App.java** with the following.

   ```java
   private static void sendMail() {
       try {
           // Send mail to the signed-in user
           // Get the user for their email address
           final User user = Graph.getUser();
           final String email = user.getMail() == null ? user.getUserPrincipalName() : user.getMail();

           Graph.sendMail("Testing Microsoft Graph", "Hello world!", email);
           System.out.println("\nMail sent.");
       } catch (Exception e) {
           System.out.println("Error sending mail");
           System.out.println(e.getMessage());
       }
   }
   ```

3. Run the app, sign in, and choose option 3 to send an email to yourself.

   ```bash
   Please choose one of the following options:
   0. Exit
   1. Display access token
   2. List my inbox
   3. Send mail
   4. Make a Graph call
   3

   Mail sent.
   ```


   Note


   If you're testing with a developer tenant from the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program), the email you send might not be delivered, and you might receive a nondelivery report. If you want to unblock sending mail from your tenant, contact support via the [Microsoft 365 admin center](https://admin.microsoft.com/).

4. To verify the message was received, choose option 2 to list your inbox.

### sendMail explained

Consider the code in the `sendMail` function.

#### Sending mail

The function uses the `_userClient.me().sendMail()` request builder, which builds a request to the [Send mail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) API. The request builder takes a `SendMailPostRequestBody` object containing the message to send.

#### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To create items with the client library, you create an instance of the class representing the data \(in this case, `com.microsoft.graph.models.Message`\) using the `new` keyword, set the desired properties, then send it in the API call. Because the call is sending data, the `post` method is used instead of `get`.

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/java-extend-app)
