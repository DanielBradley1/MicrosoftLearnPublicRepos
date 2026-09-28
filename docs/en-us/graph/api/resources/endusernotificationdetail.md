<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# endUserNotificationDetail resource type

Namespace: microsoft.graph

Represents details about end user language-specific content.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailContent | String | Email HTML content. |
| id | String | Unique identifier for the **endUserNotificationDetail** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isDefaultLangauge | Boolean | Indicates whether this language is default. |
| language | String | Notification language. |
| locale | String | Notification locale. |
| sentFrom | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Email details of the sender. |
| subject | String | Mail subject. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.endUserNotificationDetail",
  "emailContent": "String",
  "id": "String (identifier)",
  "isDefaultLangauge": "Boolean",
  "language": "String",
  "locale": "String",
  "sentFrom": {"@odata.type": "microsoft.graph.emailIdentity"},
  "subject": "String"
}
```
