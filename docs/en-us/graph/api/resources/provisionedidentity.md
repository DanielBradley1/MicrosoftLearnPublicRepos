<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisionedidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# provisionedIdentity resource type

Namespace: microsoft.graph

Describes the identity associated with the provisioning object summary event. This object is configured in the **sourceIdentity** and **targetIdentity** properties of [provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| details | [detailsInfo](https://learn.microsoft.com/en-us/graph/api/resources/detailsinfo?view=graph-rest-1.0) | Details of the identity. |
| displayName | String | Display name of the identity. Supports `$filter` \(`eq`, `contains`\). |
| id | String | Uniquely identifies the identity. Supports `$filter` \(`eq`, `contains`\). |
| identityType | String | Type of identity that has been provisioned, such as 'user' or 'group'. Supports `$filter` \(`eq`, `contains`\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "details": {
    "@odata.type": "microsoft.graph.detailsInfo"
  },
  "displayName": "String",
  "id": "String",
  "identityType": "String"
}
```
