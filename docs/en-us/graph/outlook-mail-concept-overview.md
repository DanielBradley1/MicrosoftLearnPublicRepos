<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-mail-concept-overview -->
<!-- Sitemap-Last-Modified: 2026-05-11 -->

# Outlook mail API overview

Outlook is a messaging communication hub in Microsoft 365. It also lets you manage contacts, schedule meetings, find information about users in an organization, initiate online conversations, share files, and collaborate in groups.

<iframe src="https://www.youtube-nocookie.com/embed/L-gm25wusIQ" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Why integrate with Outlook mail?

### Integrate with rich features and reach hundreds of millions of customers

Integrating with Outlook means tapping into the rich experience that customers love - consistent, intuitive experience for mail, [contacts](https://learn.microsoft.com/en-us/graph/outlook-contacts-concept-overview), [calendar](https://learn.microsoft.com/en-us/graph/outlook-calendar-concept-overview), available on all devices - mobile, web, and desktop.

Using [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview), you can integrate with Outlook by writing an app just once and reach more than hundreds of millions of consumers, and tens of millions of organization customers who choose Outlook as their email client. You can write apps that focus on mail scenarios, or connect to a wealth of other Outlook and non-Outlook relationships, resources, and intelligence, and realize scenarios supported by the Microsoft cloud.

### Automate message organization and processing

Customers like how Outlook helps them stay organized. Microsoft Graph brings these features to app developers, enabling them to build customer workflows that optimize on discovery and improve efficiency and productivity:

- Customers organize their messages in different ways - some leave all messages in the Inbox and simply search for them, others file their messages in folders. They like Outlook's flexible and intuitive approach that supports both flat and folder-based organizations. Apps can conveniently [filter, search, or sort](https://learn.microsoft.com/en-us/graph/query-parameters) messages in specific folders or the user's entire mailbox.
- Outlook categories are differentiated by name and color. Categories allow customers to tag messages to enhance organization and discovery. Apps can access and [define a user's master list of categories](https://learn.microsoft.com/en-us/graph/api/outlookuser-post-mastercategories). More, that list is shared across Outlook messages, as well as events, contacts, tasks, and group posts, and opens up creative scenarios for app developers. For example, an online training provider can color-code the emails, course events, and follow-up assignments for each course a user has enrolled in.
- Additionally, app users can change the importance of a message \(or event or task\), or flag a message for follow-up. \(Flagging is currently [in preview](https://learn.microsoft.com/en-us/graph/versioning-and-support#beta-version) in Microsoft Graph.\)
- The rules API takes message organization to the next level. Apps can set up [Inbox rules](https://learn.microsoft.com/en-us/graph/api/resources/messagerule) to promptly handle incoming messages and reduce email clutter. For example, an app can automatically move messages to another folder if their subject lines contain certain keywords, and assign categories and importance to make them easier for later follow-up.
- Many customers use email clients that send and receive messages in MIME format. Even though Outlook does not save messages in MIME format, apps can [get the body of an Outlook message in MIME format](https://learn.microsoft.com/en-us/graph/outlook-get-mime-message), [send Outlook messages in MIME format](https://learn.microsoft.com/en-us/graph/outlook-send-mime-message), attach S/MIME digital signatures, and encrypt message content in S/MIME.

### Write smarter apps that leverage intelligence

Use Microsoft Graph to suggest contextual data to your app users:

- Integrate with [Focused Inbox](https://learn.microsoft.com/en-us/graph/api/resources/manage-focused-inbox) and [@-mentions \(preview\)](https://learn.microsoft.com/en-us/graph/api/message-get?view=graph-rest-beta&preserve-view=true#example-2-get-all-mentions-in-a-specific-message) and let your app users read and respond to what's relevant to them first.
- Check [mail tips](https://learn.microsoft.com/en-us/graph/api/resources/mailtips) while still composing a message to get useful status information about a recipient \(such as the recipient sending an auto-reply or has a full mailbox\). Mail tips can alert apps of certain conditions so to take more efficient follow-up actions instead.
- Make use of the [people API](https://learn.microsoft.com/en-us/graph/people-insights-overview) to provide interactive controls such as a people picker in your app. The people API can suggest persons most relevant to a user, based on the user’s communication and collaboration patterns and business relationships.
- Offer app users a smart file picker and suggest files that they have recently interacted with, to add as attachments when composing a message. [Insights](https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights) use advanced analytics to suggest files that are trending around a user, recently viewed or edited by the user, or shared with the user.

### Store app data in a resource or resource instance

Often times apps have to store their data in an external data store and entail overhead in managing and accessing the data. Microsoft Graph lets you simply include app data as Internet message headers when [creating](https://learn.microsoft.com/en-us/graph/api/user-post-messages#example-2-create-message-draft-that-includes-custom-message-headers) or [sending](https://learn.microsoft.com/en-us/graph/api/user-sendmail#example-2-create-a-message-with-custom-internet-message-headers-and-send-the-message) a new message, or a reply to a message.

If you need to add and subsequently update custom data, you can [store the data in individual resource instances](https://learn.microsoft.com/en-us/graph/extensibility-overview). If appropriate, as an alternative, you can extend the schema, add custom properties, and store typed data in Microsoft Graph resources. You can make such [schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview) discoverable and shareable.

## Where is the data?

The Microsoft Graph API supports accessing data in users' *primary* mailboxes and in [shared mailboxes](https://support.office.com/article/open-and-use-a-shared-mailbox-in-outlook-d94a8e9e-21f1-4240-808b-de9c9c088afd). The data can be calendar, mail, or personal contacts stored in a mailbox in the cloud on Exchange Online as part of Microsoft 365.

The API does *not* support accessing in-place archive mailboxes, not [on Exchange Online](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-archiving-service-description/exchange-online-archiving-service-description#feature-availability-across-exchange-online-archiving-plans) nor [on Exchange Server](https://learn.microsoft.com/en-us/exchange/policy-and-compliance/in-place-archiving/in-place-archiving).

## API reference

Looking for the API reference for this service?

- [Outlook mail API in Microsoft Graph v1.0](https://learn.microsoft.com/en-us/graph/api/resources/mail-api-overview)
- [Outlook mail API in Microsoft Graph beta](https://learn.microsoft.com/en-us/graph/api/resources/mail-api-overview?view=graph-rest-beta&preserve-view=true)

## Next step

- Select and try Outlook mail sample queries in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer/?request=me%2Fmessages&version=v1.0). Choose **Show more samples** in the column on the left. Use the menu to turn on **Outlook Mail**.
