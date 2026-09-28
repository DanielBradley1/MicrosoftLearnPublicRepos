<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipcustomerparticipant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# delegatedAdminRelationshipCustomerParticipant resource type

Namespace: microsoft.graph

Represents identification details of a customer in a delegated admin relationship.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the customer tenant as set by Microsoft Entra ID. Read-only |
| tenantId | String | The Microsoft Entra ID-assigned tenant ID of the customer tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminRelationshipCustomerParticipant",
  "tenantId": "String",
  "displayName": "String"
}
```
