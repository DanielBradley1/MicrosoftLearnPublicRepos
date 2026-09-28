<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workplacesensoreventvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# workplaceSensorEventValue resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the data collected and reported by a badge-swiping device.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventType | [workplaceSensorEventType](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensoreventvalue?view=graph-rest-beta#workplacesensoreventtype-values) | The type of possible sensor event value. The possible values are: `badgeIn`, `badgeOut`, `unknownFutureValue`. |
| user | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-beta) | The unique identifier of a user. It could be an email or a Microsoft Entra ID. |

### workplaceSensorEventType values

| Member | Description |
| :--- | :--- |
| badgeIn | An event in which a user enters a place by swiping the badge. |
| badgeOut | An event in which a user exits a place by swiping the badge. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workplaceSensorEventValue",
  "eventType": "String",
  "user": {"@odata.type": "microsoft.graph.emailIdentity"}
}
```
