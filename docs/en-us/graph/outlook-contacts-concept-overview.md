<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-contacts-concept-overview -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Outlook personal contacts API overview

Outlook contacts lets you store personal contacts' data, and is part of the Outlook messaging hub in Microsoft 365. Through Outlook, you can manage emails, schedule meetings, find information about users in an organization, initiate online conversations, share files, and collaborate in groups.

## Why integrate with Outlook personal contacts?

### Complement messaging and calendaring scenarios for hundreds of millions of customers

Hundreds of millions of consumers and tens of millions of organization customers choose Outlook as their email client. Contacts provide a complementary function for messaging and calendaring by letting customers maintain a convenient, integrated store of contacts data within Outlook. For developers, tapping into the rich functionality of [mail](https://learn.microsoft.com/en-us/graph/outlook-mail-concept-overview) or [calendar](https://learn.microsoft.com/en-us/graph/outlook-calendar-concept-overview) means opening up richer scenarios with the user's contacts data.

### Automate contact organization

The contacts API lets you keep your customers organized, in close parity as the customers do it themselves through Outlook:

- Similarly to the customer experience, you can create [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) instances and assign them to [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder) objects.
- The contacts API lets you assign categories contacts, as well as events, messages, tasks, and group posts in a consistent way to enhance organization and discovery. In addition, you can [define a user's master list of categories](https://learn.microsoft.com/en-us/graph/api/outlookuser-post-mastercategories), which can open up additional creative scenarios.
- You can set a flag on a [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) for follow-up. \(Flagging is currently [in preview](https://learn.microsoft.com/en-us/graph/versioning-and-support#beta-version) in Microsoft Graph.\)

### Share contact information

The contacts API lets you get contact items of the signed-in user, or of the users who have shared or delegated their contacts to the signed-in user. For example, if Garth has shared a contact folder with John, or if Garth has delegated access to John, then [delegated permissions](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#microsoft-graph-permissions) from John would give you read access to Garth's shared calendar and contents as well.

### Leverage people API in Microsoft Graph to make better use of all people data

You can use the typical CRUD operations for an Outlook [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) to create and manage contacts. As part of Microsoft Graph, you can also use the [people API](https://learn.microsoft.com/en-us/graph/people-insights-overview) that looks at a user's Outlook contacts, as well as social networks, organization directory, and people from recent communication, and return information about people from all these sources that are most relevant to the user. Take advantage of this additional intelligence in people picker scenarios.

### Take advantage of other shared features and conveniences in Microsoft Graph

- The **contact** entity supports a contact photo which is implemented as the same [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto) entity as a user photo stored in Exchange Online or Microsoft Entra ID. This eliminates the overhead in converting between contact and user profile photos.
- You can keep the app local store synchronized by subscribing to [change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview) and [tracking changes](https://learn.microsoft.com/en-us/graph/delta-query-overview) to contacts and contact folders.
- You can extend app storage in a contact instance as an [open extension](https://learn.microsoft.com/en-us/graph/extensibility-overview#4-open-extensions), or add strongly typed custom data to the contact schema as a [schema extension](https://learn.microsoft.com/en-us/graph/extensibility-overview#3-schema-extensions).

## Where is the data?

The Microsoft Graph API supports accessing data in users' *primary* mailboxes and in [shared mailboxes](https://support.office.com/article/open-and-use-a-shared-mailbox-in-outlook-d94a8e9e-21f1-4240-808b-de9c9c088afd). The data can be calendar, mail, or personal contacts stored in a mailbox in the cloud on Exchange Online as part of Microsoft 365.

The API does *not* support accessing in-place archive mailboxes, not [on Exchange Online](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-archiving-service-description/exchange-online-archiving-service-description#feature-availability-across-exchange-online-archiving-plans) nor [on Exchange Server](https://learn.microsoft.com/en-us/exchange/policy-and-compliance/in-place-archiving/in-place-archiving).

## API reference

Looking for the API reference for this service?

- [Outlook contacts API in Microsoft Graph v1.0](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0&preserve-view=true)
- [Outlook contacts API in Microsoft Graph beta](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-beta&preserve-view=true)

## Next steps

- Select and try contacts sample queries in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer/?request=me%2Fcontacts&version=v1.0). Choose **Show more samples** in the column on the left. Use the menu to turn on **Personal contacts**.
- Learn about:

  - [Getting immutable identifiers for Outlook resources](https://learn.microsoft.com/en-us/graph/outlook-immutable-id)
  - [Getting shared contacts](https://learn.microsoft.com/en-us/graph/outlook-get-shared-contacts-folders)
