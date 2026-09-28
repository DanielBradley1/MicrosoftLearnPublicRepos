<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-19 -->

# teamTemplate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a logical container for all the definitions and versions of the same team template.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List teamTemplates](https://learn.microsoft.com/en-us/graph/api/teamwork-list-teamtemplates?view=graph-rest-beta) | [teamTemplate](https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta) collection | Get a list of the **teamTemplate** objects available for the tenant. |
| [List definitions](https://learn.microsoft.com/en-us/graph/api/teamtemplate-list-definitions?view=graph-rest-beta) | [teamTemplateDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta) collection | List the [teamTemplateDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamstemplate?view=graph-rest-beta) objects associated with a **teamTemplate**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the template. Cannot be null. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitions | [teamtemplatedefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta) collection | A generic representation of a team template definition for a team with a specific structure and configuration. |

## JSON representation

```json
{
  "id": "string"
}
```

## Related content

- [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-beta)
- [teamTemplateDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamtemplatedefinition?view=graph-rest-beta)
