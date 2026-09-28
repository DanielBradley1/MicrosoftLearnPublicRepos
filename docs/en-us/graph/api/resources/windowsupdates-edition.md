<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-edition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# edition resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a specific edition of a Windows product, such as Enterprise, Core, or Education.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceFamily | String | The device family targeted by the edition. |
| endOfServiceDateTime | DateTimeOffset | The date and time when the edition reached the end of service. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| generalAvailabilityDateTime | DateTimeOffset | The date and time when the edition became available to the general customers for the first time. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier for the edition entry. Read-only. |
| isInService | Boolean | Indicates whether the edition is in service or out of service. |
| name | String | The name of the edition. Read-only. |
| releasedName | String | The public name of the edition. Read-only. |

## Relationships

| Relationships | Type | Description |
| :--- | :--- | :--- |
| servicingPeriods | [microsoft.graph.windowsUpdates.servicingPeriod](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-servicingperiod?view=graph-rest-beta) collection | Each object holds information of a servicing period related to the product edition. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.edition",
  "deviceFamily": "String",
  "endOfServiceDateTime": "String (timestamp)",
  "generalAvailabilityDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isInService": "Boolean",
  "name": "String",
  "releasedName": "String"
}
```
