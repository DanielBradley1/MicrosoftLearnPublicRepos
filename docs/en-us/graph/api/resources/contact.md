<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# contact resource type

Namespace: microsoft.graph

A contact is an item in Outlook where you can organize and save information about the people and organizations you communicate with. Contacts are contained in contact folders.

This resource supports:

- Adding your own data to custom properties as [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).
- Subscribing to [change notifications](https://learn.microsoft.com/en-us/graph/change-notifications-overview).
- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/contact-delta?view=graph-rest-1.0) function.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get contact](https://learn.microsoft.com/en-us/graph/api/contact-get?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Read properties and relationships of contact object. |
| [Create contact](https://learn.microsoft.com/en-us/graph/api/user-post-contacts?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Add a contact to the root Contacts folder or the contacts endpoint of another contact folder. |
| [Update contact](https://learn.microsoft.com/en-us/graph/api/contact-update?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Update contact object. |
| [Delete contact](https://learn.microsoft.com/en-us/graph/api/contact-delete?view=graph-rest-1.0) | None | Delete contact object. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/contact-permanentdelete?view=graph-rest-1.0) | None | Permanently delete a contact and place it in the purges folder in the recoverable Items folder in the user's mailbox. |
| [Get contact delta](https://learn.microsoft.com/en-us/graph/api/contact-delta?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) collection | Get a set of contacts that have been added, deleted, or updated in a specified folder. |
| **Open extensions** |  |  |
| [Create open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-post-opentypeextension?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) | Create an open extension and add custom properties in a new or existing instance of a resource. |
| [Get open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-get?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) collection | Get an open extension object or objects identified by name or fully qualified name. |
| **Extended properties** |  |  |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Create one or more single-value extended properties in a new or existing contact. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Get contacts that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Create one or more multi-value extended properties in a new or existing contact. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Get a contact that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assistantName | String | The name of the contact's assistant. |
| birthday | DateTimeOffset | The contact's birthday. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| businessAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The contact's business address. |
| businessHomePage | String | The business home page of the contact. |
| businessPhones | String collection | The contact's business phone numbers. |
| categories | String collection | The categories associated with the contact. |
| changeKey | String | Identifies the version of the contact. Every time the contact is changed, ChangeKey changes as well. This allows Exchange to apply changes to the correct version of the object. |
| children | String collection | The names of the contact's children. |
| companyName | String | The name of the contact's company. |
| createdDateTime | DateTimeOffset | The time the contact was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| department | String | The contact's department. |
| displayName | String | The contact's display name. You can specify the display name in a [create](https://learn.microsoft.com/en-us/graph/api/user-post-contacts?view=graph-rest-1.0) or [update](https://learn.microsoft.com/en-us/graph/api/contact-update?view=graph-rest-1.0) operation. Note that later updates to other properties may cause an automatically generated value to overwrite the displayName value you have specified. To preserve a pre-existing value, always include it as displayName in an [update](https://learn.microsoft.com/en-us/graph/api/contact-update?view=graph-rest-1.0) operation. |
| emailAddresses | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) collection | The contact's email addresses. |
| fileAs | String | The name the contact is filed under. |
| generation | String | The contact's suffix. |
| givenName | String | The contact's given name. |
| homeAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The contact's home address. |
| homePhones | String collection | The contact's home phone numbers. |
| id | String | The contact's unique identifier. By default, this value changes when the item is moved from one container \(such as a folder or calendar\) to another. To change this behavior, use the `Prefer: IdType="ImmutableId"` header. See [Get immutable identifiers for Outlook resources](https://learn.microsoft.com/en-us/graph/outlook-immutable-id) for more information. Read-only. |
| imAddresses | String collection | The contact's instant messaging \(IM\) addresses. |
| initials | String | The contact's initials. |
| jobTitle | String | The contact’s job title. |
| lastModifiedDateTime | DateTimeOffset | The time the contact was modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| manager | String | The name of the contact's manager. |
| middleName | String | The contact's middle name. |
| mobilePhone | String | The contact's mobile phone number. |
| nickName | String | The contact's nickname. |
| officeLocation | String | The location of the contact's office. |
| otherAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | Other addresses for the contact. |
| parentFolderId | String | The ID of the contact's parent folder. |
| personalNotes | String | The user's notes about the contact. |
| primaryEmailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The contact's primary email address. |
| profession | String | The contact's profession. |
| secondaryEmailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The contact's secondary email address. |
| spouseName | String | The name of the contact's spouse/partner. |
| surname | String | The contact's surname. |
| tertiaryEmailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The contact's tertiary email address. |
| title | String | The contact's title. |
| yomiCompanyName | String | The phonetic Japanese company name of the contact. |
| yomiGivenName | String | The phonetic Japanese given name \(first name\) of the contact. |
| yomiSurname | String | The phonetic Japanese surname \(last name\) of the contact. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the contact. Read-only. Nullable. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the contact. Read-only. Nullable. |
| photo | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) | Optional contact picture. You can get or set a photo for a contact. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the contact. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assistantName": "string",
  "birthday": "String (timestamp)",
  "businessAddress": {"@odata.type": "microsoft.graph.physicalAddress"},
  "businessHomePage": "string",
  "businessPhones": ["string"],
  "categories": ["string"],
  "changeKey": "string",
  "children": ["string"],
  "companyName": "string",
  "createdDateTime": "String (timestamp)",
  "department": "string",
  "displayName": "string",
  "emailAddresses": [{"@odata.type": "microsoft.graph.emailAddress"}],
  "fileAs": "string",
  "generation": "string",
  "givenName": "string",
  "homeAddress": {"@odata.type": "microsoft.graph.physicalAddress"},
  "homePhones": ["string"],
  "id": "string (identifier)",
  "imAddresses": ["string"],
  "initials": "string",
  "jobTitle": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "manager": "string",
  "middleName": "string",
  "mobilePhone": "string",
  "nickName": "string",
  "officeLocation": "string",
  "otherAddress": {"@odata.type": "microsoft.graph.physicalAddress"},
  "parentFolderId": "string",
  "personalNotes": "string",
  "photo": { "@odata.type": "microsoft.graph.profilePhoto" },
  "primaryEmailAddress": {"@odata.type": "microsoft.graph.emailAddress"},
  "profession": "string",
  "secondaryEmailAddress": {"@odata.type": "microsoft.graph.emailAddress"},
  "spouseName": "string",
  "surname": "string",
  "tertiaryEmailAddress": {"@odata.type": "microsoft.graph.emailAddress"},
  "title": "string",
  "yomiCompanyName": "string",
  "yomiGivenName": "string",
  "yomiSurname": "string"
}
```

## Related content

- [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview)
- [Get incremental changes to messages in a folder](https://learn.microsoft.com/en-us/graph/delta-query-messages)
- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
