<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# ticketInfo resource type

Namespace: microsoft.graph

Represents ticket information related to assignment and eligibility requests in [PIM for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-1.0) and [PIM for Groups](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagement-for-groups-api-overview?view=graph-rest-1.0). Use this object to define ticket parameters for an assignment or eligibility request that's initiated by another request made in an external system.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ticketNumber | String | The ticket number. |
| ticketSystem | String | The description of the ticket system. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ticketInfo",
  "ticketNumber": "String",
  "ticketSystem": "String"
}
```
