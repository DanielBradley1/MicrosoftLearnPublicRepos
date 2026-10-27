<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policylocationagent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# policyLocationAgent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an agent application to which a data loss prevention policy applies.

Used for the **applicationLocation** property of [protectedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/protectedapplicationmetadata?view=graph-rest-beta) and in the **locations** parameter of [tenantProtectionScopeContainer: compute](https://learn.microsoft.com/en-us/graph/api/tenantprotectionscopecontainer-compute?view=graph-rest-beta).

Inherits from [policyLocationApplication](https://learn.microsoft.com/en-us/graph/api/resources/policylocationapplication?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentMetadata | [agentMetadata](https://learn.microsoft.com/en-us/graph/api/resources/agentmetadata?view=graph-rest-beta) | Metadata used for agent policy scoping and evaluation. Optional. |
| value | String | The Microsoft Entra application ID or other primary identifier of the agent. Inherited from [policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-beta). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyLocationAgent",
  "agentMetadata": {
    "@odata.type": "microsoft.graph.agentMetadata"
  },
  "value": "String"
}
```
