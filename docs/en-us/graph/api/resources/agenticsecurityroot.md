<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agenticsecurityroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# agenticSecurityRoot resource type

Namespace: microsoft.graph

Provides access to playbook definitions and agentic security sessions. Use its child collections; reading, updating, or deleting this container directly isn't supported.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List playbookDefinitions](https://learn.microsoft.com/en-us/graph/api/agenticsecurityroot-list-playbookdefinitions?view=graph-rest-beta) | [playbookDefinition](https://learn.microsoft.com/en-us/graph/api/resources/playbookdefinition?view=graph-rest-beta) collection | Get the playbook catalog. |
| [List sessions](https://learn.microsoft.com/en-us/graph/api/agenticsecurityroot-list-sessions?view=graph-rest-beta) | [investigationSession](https://learn.microsoft.com/en-us/graph/api/resources/investigationsession?view=graph-rest-beta) collection | Get the caller's sessions. |
| [Create session](https://learn.microsoft.com/en-us/graph/api/agenticsecurityroot-post-sessions?view=graph-rest-beta) | [investigationSession](https://learn.microsoft.com/en-us/graph/api/resources/investigationsession?view=graph-rest-beta) | Start a playbook execution. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique, read-only identifier of the resource. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| playbookDefinitions | [playbookDefinition](https://learn.microsoft.com/en-us/graph/api/resources/playbookdefinition?view=graph-rest-beta) collection | The read-only playbook catalog. Supports list and keyed GET with `$select`. Doesn't support `$filter`, `$orderby`, `$search`, `$expand`, `$count`, `$top`, `$skip`, or delta tracking. |
| sessions | [investigationSession](https://learn.microsoft.com/en-us/graph/api/resources/investigationsession?view=graph-rest-beta) collection | The agentic sessions visible to the caller. Supports list with `$filter` on **status** \(`eq`, `or`, `in`\), `$top`, and `$select`; session creation; and keyed reads. Doesn't support `$count`, `$orderby`, `$search`, `$expand`, `$skip`, or delta tracking. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agenticSecurityRoot",
  "id": "String (identifier)"
}
```
