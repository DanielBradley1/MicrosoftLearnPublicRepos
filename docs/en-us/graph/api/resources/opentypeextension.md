<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# openTypeExtension resource type \(open extensions\)

Namespace: microsoft.graph

Represents open extensions \(also known as open type extensions, and formerly known as Office 365 data extensions\), an [extensibility option](https://learn.microsoft.com/en-us/graph/extensibility-overview) that provides an easy way to directly add untyped properties to a resource in Microsoft Graph.

Any open extension added to a resource shows up in the **extensions** navigation property. Each extension has an **extensionName** property that is the only predefined, writable property for all extensions, along with your custom data. One way to help make sure extension names are unique is to use a reverse domain name system \(DNS\) format that is dependent on *your own domain*, for example, `com.contoso.ContactInfo`. **Don't use** the Microsoft domain \(`com.microsoft` or `com.onmicrosoft`\) in an extension name.

Derives from the [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) abstract type.

The following resources support open extension:

- [user](https://learn.microsoft.com/en-us/graph/api/resources/user)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group)

- [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact)
- [device](https://learn.microsoft.com/en-us/graph/api/resources/device)
- [event](https://learn.microsoft.com/en-us/graph/api/resources/event) for both user and group calendars
- [message](https://learn.microsoft.com/en-us/graph/api/resources/message)
- [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0)
- [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization)
- [post](https://learn.microsoft.com/en-us/graph/api/resources/post)
- [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0)
- [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0)

> **Note:** \* Due to an existing service limitation, delegates can't create open extension-appended events in shared mailbox calendars. Attempts to do so will result in an `ErrorAccessDenied` response.

For more information about Microsoft Graph extensibility including limits for open extensions, see [Add custom properties to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview) and [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users).

### Outlook-specific considerations

Each open extension on an Outlook resource \(event, message, or personal contact\) is stored in a [MAPI named property](https://learn.microsoft.com/en-us/office/client-developer/outlook/mapi/mapi-named-properties). When you create open extensions for Outlook, consider that MAPI named properties are a finite resource in a user's mailbox. When a user's named property quota is exhausted, you can't create anymore named properties for that user. This can result in unexpected behavior from clients that rely on named properties to function.

Apply the following guidelines when you create open extensions on Outlook resources:

- Create the minimum number of extensions required. Most applications should require no more than one extension. Extensions have no defined properties or structure, so you can store multiple values in a single extension.
- Avoid naming extensions in a variable manner \(such as based on user input, etc.\). Each time an open extension is created with a new name that hasn't been used in a user's mailbox before, a new MAPI named property is created. Removing the extension doesn't remove the named property.

### Use open extensions \(for Outlook resources\) or extended properties

Open extensions are the recommended solution for most scenarios involving storing and accessing custom data. If, however, you need to access custom data for Outlook MAPI properties that aren't already exposed through the [Microsoft Graph API metadata](https://learn.microsoft.com/en-us/graph/traverse-the-graph#microsoft-graph-api-metadata), you can use [extended properties and its REST API](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0). You can verify which properties the metadata exposes at `https://graph.microsoft.com/v1.0/$metadata`.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/opentypeextension-post-opentypeextension?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0)\(in an existing resource instance\), or a new [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0), [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0), [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0), or [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) that contains an openTypeExtension object. | Create an openTypeExtension object in an existing or new resource instance. |
| [Get](https://learn.microsoft.com/en-us/graph/api/opentypeextension-get?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) | Read properties and relationships of openTypeExtension object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/opentypeextension-update?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) | Update openTypeExtension object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/opentypeextension-delete?view=graph-rest-1.0) | None | Delete openTypeExtension object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| extensionName | String | A unique text identifier for an open type data extension. Optional. |
| id | String | A fully qualified identifier that concatenates the extension type with the **extensionName**. Read-only.  <br>  <br>The **id** must be defined during the *Create* operation via one of the following ways:<br><br>- Explicitly define the **id** property in the request body.<br>- Define an **extensionName** property in the request body, and Microsoft Graph automatically assigns the same value to the **id** property.<br><br>  - In subsequent updates, you can change the **extensionName** property value to one that's different from the **id** value.<br>  - In subsequent updates, specifying only the **id** property in the request body automatically deletes the **extensionName** property from the open extension. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "extensionName": "string",
  "id": "String (identifier)"
}
```

## Related content

- [Add custom properties to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
