<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-policyidentifierdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# policyIdentifierDetail resource type

Namespace: microsoft.graph.teamsAdministration

Represents the identifier details of a Teams policy, including the policy name and its unique ID.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The display name of the policy instance. |
| policyId | String | The unique ID associated with the policy instance. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.policyIdentifierDetail",
  "name": "String",
  "policyId": "String"
}
```
