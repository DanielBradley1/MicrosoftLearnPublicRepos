<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/powershell-email -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Add email capabilities to PowerShell scripts using Microsoft Graph

In this article, you extend the application you created in [Build PowerShell scripts with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/powershell) with Microsoft Graph mail APIs. You use Microsoft Graph to list the user's inbox and send an email.

## List user's inbox

Start by listing messages in the user's email inbox.

1. In your authenticated PowerShell session, verify that the `$user` variable is set.

   ```powershell
   PS > $user.DisplayName
   Megan Bowen
   ```

2. Run the following command to list the user's inbox.

   ```powershell
   Get-MgUserMailFolderMessage -UserId $user.Id -MailFolderId Inbox -Select `
     "from,isRead,receivedDateTime,subject" -OrderBy "receivedDateTime DESC" `
     -Top 25 | Format-Table Subject,@{n='From';e={$_.From.EmailAddress.Name}}, `
     IsRead,ReceivedDateTime
   ```

3. Review the output.

   ```powershell
   Subject                                    From                    IsRead ReceivedDateTime
   -------                                    ----                    ------ ----------------
   Updates from Ask HR and other communities  Contoso Demo on Yammer  False  4/19/2022 10:19:02 PM
   Employee Initiative Thoughts               Patti Fernandez         False  4/19/2022 3:15:56 PM
   Voice Mail (11 seconds)                    Alex Wilber             False  4/18/2022 2:24:16 PM
   Our Spring Blog Update                     Alex Wilber             True   4/18/2022 1:52:03 PM
   Atlanta Flight Reservation                 Alex Wilber             False  4/13/2022 2:30:27 AM
   Atlanta Trip Itinerary - down time         Alex Wilber             False  4/12/2022 4:46:01 PM
   ```

### List inbox code explained

Consider the command used to list the user's inbox

#### Accessing well-known mail folders

The `Get-MgUserMailFolderMessage` command builds a request to the [List messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages) API, specifically using the `GET /users/{user-id}/mailFolders/{folder-id}/messages` endpoint. The API only returns messages in the requested mail folder. In this case, because the inbox is a default, well-known folder inside a user's mailbox, it's accessible via its well-known name: `-MailFolderId Inbox`. Nondefault folders are accessed the same way, by replacing the well-known name with the mail folder's ID property. For details on the available well-known folder names, see [mailFolder resource type](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder).

#### Accessing a collection

Unlike the `Get-MgUser` command from the previous section, which returns a single object, this method returns a collection of messages. Most APIs in Microsoft Graph that return a collection don't return all available results in a single response. Instead, they use [paging](https://learn.microsoft.com/en-us/graph/paging) to return a portion of the results while providing a method for clients to request the next page.

##### Default page sizes

APIs that use paging implement a default page size. For messages, the default value is 10. Clients can request more \(or less\) by using the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top-parameter) query parameter. In the Microsoft Graph PowerShell SDK, adding `$top` is accomplished with the `-Top 25` parameter.

Note

The value passed via `-Top` is an upper-bound, not an explicit number. The API returns a number of messages *up to* the specified value.

#### Sorting collections

The function uses the `-OrderBy` parameter on the request to request results sorted by the time the message is received \(`receivedDateTime` property\). It includes the `DESC` keyword so that messages received more recently are listed first. This parameter adds the [$orderby query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#orderby-parameter) to the API call.

## Send mail

Now add the ability to send an email message as the authenticated user.

1. In your authenticated PowerShell session, verify that the `$user` variable is set.

   ```powershell
   PS > $user.DisplayName
   Megan Bowen
   ```

2. Use the following command to define an object representing the request body for the [Send mail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) API.

   ```powershell
   $sendMailParams = @{
       Message = @{
           Subject = "Testing Microsoft Graph"
           Body = @{
               ContentType = "text"
               Content = "Hello world!"
           }
           ToRecipients = @(
               @{
                   EmailAddress = @{
                       Address = ($user.Mail ?? $user.UserPrincipalName)
                   }
               }
           )
       }
   }
   ```

3. Use the following command to send the message.

   ```powershell
   Send-MgUserMail -UserId $user.Id -BodyParameter $sendMailParams
   ```


   Note


   If you're testing with a developer tenant from the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program), the email you send might not be delivered, and you might receive a nondelivery report. If you want to unblock sending mail from your tenant, contact support via the [Microsoft 365 admin center](https://admin.microsoft.com/).

4. To verify the message was received, repeat the `Get-MgUserMailFolderMessage` command from the previous step.

### Send mail code explained

Consider the commands used to send a message.

#### Sending mail

The `Send-MgUserMail` command builds a request to the [Send mail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) API.

#### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To create items with the SDK, you create an object representing the request body, set the desired properties, then pass it in the `BodyParameter` parameter.

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/powershell-extend-app)
