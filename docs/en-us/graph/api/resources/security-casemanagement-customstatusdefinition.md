<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customstatusdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# customStatusDefinition resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom status returned inline within a top-level [statusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta). Because it's an inline complex type rather than an entity, a custom status isn't separately addressable and carries its own **customStatusId** rather than an **id**.

A case that's in a final custom status can't transition to another status. A custom status that was never marked final is treated as not final.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customStatusId | String | The immutable identifier of the custom status. |
| displayName | String | The human-readable label of the custom status. |
| isFinal | Boolean | `true` if this is a terminal status; a case in a final status can't transition to another status. Otherwise, `false`. |
| sortOrder | Int32 | The display order of the custom status within its parent status. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.customStatusDefinition",
  "customStatusId": "String",
  "displayName": "String",
  "sortOrder": "Int32",
  "isFinal": "Boolean"
}
```
