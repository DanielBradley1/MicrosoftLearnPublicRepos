<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamTemplateDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Generic representation of a team template definition for a team with a specific structure and configuration.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamtemplatedefinition-get?view=graph-rest-beta) | [teamTemplateDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta) | Read the properties and relationships of a [teamTemplateDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/teamtemplate-list-definitions?view=graph-rest-beta) | [teamTemplateDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta) collection | List the **teamTemplateDefinition** objects associated with a **teamTemplate**. |
| [Get team definition](https://learn.microsoft.com/en-us/graph/api/teamtemplatedefinition-get-teamdefinition?view=graph-rest-beta) | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-beta) | Read the properties of the **team** of a **teamTemplateDefinition** object |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| audience | teamTemplateAudience | Describes the audience the team template is available to. The possible values are: `organization`, `user`, `public`, `unknownFutureValue`. |
| categories | String collection | The assigned categories for the team template. |
| description | String | A brief description of the team template as it will appear to the users in Microsoft Teams. |
| displayName | String | The user defined name of the team template. |
| iconUrl | String | The icon url for the team template. |
| id | String | Encoded64 of `templateId` + `audience` + `locale` for the team template. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| languageTag | String | Language the template is available in. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user who last modified the team template. |
| lastModifiedDateTime | DateTimeOffset | The date time of when the team template was last modified. |
| parentTemplateId | String | The `templateId` for the team template |
| publisherName | String | The organization which published the team template. |
| shortDescription | String | A short-description of the team template as it will appear to the users in Microsoft Teams. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| teamDefinition | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-beta) | Collection of [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-beta) objects. A channel represents a topic, and therefore a logical isolation of discussion, within a team. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamTemplateDefinition",
  "audience": "String",
  "categories": [
    "String"
  ],
  "description": "String",
  "displayName": "String",
  "iconUrl": "String",
  "id": "String (identifier)",
  "languageTag": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "parentTemplateId": "String",
  "publisherName": "String", 
  "shortDescription": "String"
}
```

## Related content

- [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-beta)
- [teamsTemplate](https://learn.microsoft.com/en-us/graph/api/resources/teamstemplate?view=graph-rest-beta)
