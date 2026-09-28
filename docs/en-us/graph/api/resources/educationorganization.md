<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# educationOrganization resource type

Namespace: microsoft.graph

Abstract entity used to model the commonality between different organization types within the education sector.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Organization description. |
| displayName | String | Organization display name. |
| externalSource | educationExternalSource | Source where this organization was created from. The possible values are: `sis`, `manual`. |
| externalSourceDetail | String | The name of the external source this resource was generated from. |
| id | String | Object identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationOrganization",
  "displayName": "String",
  "description": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "id": "String (identifier)"
}
```
