<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# trainingLanguageDetail resource type

Namespace: microsoft.graph

Represents language information for an attack simulation training.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/traininglanguagedetail-get?view=graph-rest-1.0) | [trainingLanguageDetail](https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0) | Get the [language details](https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0) about an attack simulation training for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | Language specific content for the training. |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the language details. |
| createdDateTime | DateTimeOffset | Date and time when the language details were created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Description as defined by the user. |
| displayName | String | Display name as defined by the user. |
| id | String | Unique identifier of the **trainingLanguageDetail** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isDefaultLangauge | Boolean | Indicates whether the training has a default language. |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who last modified the details. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the **trainingLanguageDetail** was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| locale | String | Content locale for the training detail. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingLanguageDetail",
  "content": "String",
  "createdBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isDefaultLangauge": "Boolean",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "lastModifiedDateTime": "String (timestamp)",
  "locale": "String"
}
```
