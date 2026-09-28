<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/go-email -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add email capabilities to Go apps using Microsoft Graph

In this article, you extend the application you created in [Build Go apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/go) with Microsoft Graph mail APIs. You use Microsoft Graph to list the user's inbox and send an email.

## List user's inbox

Start by listing messages in the user's email inbox.

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) GetInbox() (models.MessageCollectionResponseable, error) {
       var topValue int32 = 25
       query := users.ItemMailFoldersItemMessagesRequestBuilderGetQueryParameters{
           // Only request specific properties
           Select: []string{"from", "isRead", "receivedDateTime", "subject"},
           // Get at most 25 results
           Top: &topValue,
           // Sort by received time, newest first
           Orderby: []string{"receivedDateTime DESC"},
       }

       return g.userClient.Me().MailFolders().
           ByMailFolderId("inbox").
           Messages().
           Get(context.Background(),
               &users.ItemMailFoldersItemMessagesRequestBuilderGetRequestConfiguration{
                   QueryParameters: &query,
               })
   }
   ```

2. Replace the empty `listInbox` function in **graphtutorial.go** with the following.

   ```go
   func listInbox(graphHelper *graphhelper.GraphHelper) {
       messages, err := graphHelper.GetInbox()
       if err != nil {
           log.Panicf("Error getting user's inbox: %v", err)
       }

       // Load local time zone
       // Dates returned by Graph are in UTC, use this
       // to convert to local
       location, err := time.LoadLocation("Local")
       if err != nil {
           log.Panicf("Error getting local timezone: %v", err)
       }

       // Output each message's details
       for _, message := range messages.GetValue() {
           fmt.Printf("Message: %s\n", *message.GetSubject())
           fmt.Printf("  From: %s\n", *message.GetFrom().GetEmailAddress().GetName())

           status := "Unknown"
           if *message.GetIsRead() {
               status = "Read"
           } else {
               status = "Unread"
           }
           fmt.Printf("  Status: %s\n", status)
           fmt.Printf("  Received: %s\n", (*message.GetReceivedDateTime()).In(location))
       }

       // If GetOdataNextLink does not return nil,
       // there are more messages available on the server
       nextLink := messages.GetOdataNextLink()

       fmt.Println()
       fmt.Printf("More messages available? %t\n", nextLink != nil)
       fmt.Println()
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
     Received: 2021-12-30 04:54:54 -0500 EST
   Message: Employee Initiative Thoughts
     From: Patti Fernandez
     Status: Read
     Received: 2021-12-28 17:01:10 -0500 EST
   Message: Voice Mail (11 seconds)
     From: Alex Wilber
     Status: Unread
     Received: 2021-12-28 17:00:46 -0500 EST
   Message: Our Spring Blog Update
     From: Alex Wilber
     Status: Unread
     Received: 2021-12-28 16:49:46 -0500 EST
   Message: Atlanta Flight Reservation
     From: Alex Wilber
     Status: Unread
     Received: 2021-12-28 16:35:42 -0500 EST
   Message: Atlanta Trip Itinerary - down time
     From: Alex Wilber
     Status: Unread
     Received: 2021-12-28 16:22:04 -0500 EST

   ...

   More messages available? True
   ```

### GetInbox explained

Consider the code in the `GetInbox` function.

#### Accessing well-known mail folders

The function uses the `userClient.Me().MailFolders.ByMailFolderId("inbox").Messages()` request builder, which builds a request to the [List messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages) API. Because it includes the `ByMailFolderId("inbox")` request builder, the API only returns messages in the requested mail folder. In this case, because the inbox is a default, well-known folder inside a user's mailbox, it's accessible via its well-known name. Nondefault folders are accessed the same way, by replacing the well-known name with the mail folder's ID property. For details on the available well-known folder names, see [mailFolder resource type](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder).

#### Accessing a collection

Unlike the `GetUser` function from the previous section, which returns a single object, this method returns a collection of messages. Most APIs in Microsoft Graph that return a collection don't return all available results in a single response. Instead, they use [paging](https://learn.microsoft.com/en-us/graph/paging) to return a portion of the results while providing a method for clients to request the next page.

##### Default page sizes

APIs that use paging implement a default page size. For messages, the default value is 10. Clients can request more \(or less\) by using the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top-parameter) query parameter. In `GetInbox`, adding `$top` is accomplished with the `Top` property in the query parameters.

Note

The value passed in `Top` is an upper-bound, not an explicit number. The API returns a number of messages *up to* the specified value.

##### Getting subsequent pages

If there are more results available on the server, collection responses include an `@odata.nextLink` property with an API URL to access the next page. The Go SDK provides the `GetOdataNextLink` method on collection page objects. If this method returns non-nil, there are more results available.

#### Sorting collections

The function uses the `OrderBy` property in the query parameters to request results sorted by the time the message is received \(`receivedDateTime` property\). It includes the `DESC` keyword so that messages received more recently are listed first. The `OrderBy` property adds the [$orderby query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#orderby-parameter) to the API call.

## Send mail

Now add the ability to send an email message as the authenticated user.

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) SendMail(subject *string, body *string, recipient *string) error {
       // Create a new message
       message := models.NewMessage()
       message.SetSubject(subject)

       messageBody := models.NewItemBody()
       messageBody.SetContent(body)
       contentType := models.TEXT_BODYTYPE
       messageBody.SetContentType(&contentType)
       message.SetBody(messageBody)

       toRecipient := models.NewRecipient()
       emailAddress := models.NewEmailAddress()
       emailAddress.SetAddress(recipient)
       toRecipient.SetEmailAddress(emailAddress)
       message.SetToRecipients([]models.Recipientable{
           toRecipient,
       })

       sendMailBody := users.NewItemSendMailPostRequestBody()
       sendMailBody.SetMessage(message)

       // Send the message
       return g.userClient.Me().SendMail().Post(context.Background(), sendMailBody, nil)
   }
   ```

2. Replace the empty `sendMail` function in **graphtutorial.go** with the following.

   ```go
   func sendMail(graphHelper *graphhelper.GraphHelper) {
       // Send mail to the signed-in user
       // Get the user for their email address
       user, err := graphHelper.GetUser()
       if err != nil {
           log.Panicf("Error getting user: %v", err)
       }

       // For Work/school accounts, email is in Mail property
       // Personal accounts, email is in UserPrincipalName
       email := user.GetMail()
       if email == nil {
           email = user.GetUserPrincipalName()
       }

       subject := "Testing Microsoft Graph"
       body := "Hello world!"
       err = graphHelper.SendMail(&subject, &body, email)
       if err != nil {
           log.Panicf("Error sending mail: %v", err)
       }

       fmt.Println("Mail sent.")
       fmt.Println()
   }
   ```

3. Run the app, sign in, and choose option 3 to send an email to yourself.

   ```Shell
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

### SendMail explained

Consider the code in the `SendMail` function.

#### Sending mail

The function uses the `userClient.Me().SendMail()` request builder, which builds a request to the [Send mail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) API. The request builder takes a `Message` object representing the message to send.

#### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To create items with the client library, create an instance of the class representing the data \(in this case, `models.Message`\), set the desired properties, then send it in the API call. Because the call is sending data, the `Post` method is used instead of `Get`.

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/go-extend-app)
