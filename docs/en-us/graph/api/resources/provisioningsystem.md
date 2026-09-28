<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisioningsystem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# provisioningSystem resource type

Namespace: microsoft.graph

Represents the system that a user was provisioned to or from. For example, when provisioning a user from Microsoft Entra ID to ServiceNow, the source system is Microsoft Entra ID, and the target system is ServiceNow. This object is configured in the **sourceSystem** and **targetSystem** properties of [provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the system that a user was provisioned to or from. |
| details | [detailsInfo](https://learn.microsoft.com/en-us/graph/api/resources/detailsinfo?view=graph-rest-1.0) | Details of the system. |
| id | String | Identifier of the system that a user was provisioned to or from. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "details": {
    "@odata.type": "microsoft.graph.detailsInfo"
  },
  "displayName": "String",
  "id": "String"
}
```
