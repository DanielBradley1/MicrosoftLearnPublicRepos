<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# localizedNotificationMessage resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The text content of a Notification Message Template for the specified locale.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List localizedNotificationMessages](https://learn.microsoft.com/en-us/graph/api/intune-notification-localizednotificationmessage-list?view=graph-rest-1.0) | [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) collection | List properties and relationships of the [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) objects. |
| [Get localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/intune-notification-localizednotificationmessage-get?view=graph-rest-1.0) | [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) | Read properties and relationships of the [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) object. |
| [Create localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/intune-notification-localizednotificationmessage-create?view=graph-rest-1.0) | [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) | Create a new [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) object. |
| [Delete localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/intune-notification-localizednotificationmessage-delete?view=graph-rest-1.0) | None | Deletes a [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0). |
| [Update localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/intune-notification-localizednotificationmessage-update?view=graph-rest-1.0) | [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) | Update the properties of a [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |
| locale | String | The Locale for which this message is destined. |
| subject | String | The Message Template Subject. |
| messageTemplate | String | The Message Template content. |
| isDefault | Boolean | Flag to indicate whether or not this is the default locale for language fallback. This flag can only be set. To unset, set this property to true on another Localized Notification Message. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.localizedNotificationMessage",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "locale": "String",
  "subject": "String",
  "messageTemplate": "String",
  "isDefault": true
}
```
