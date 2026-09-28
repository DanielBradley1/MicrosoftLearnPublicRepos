<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/servicehealth?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# serviceHealth resource type

Namespace: microsoft.graph

Represents the health information of a service subscribed by a tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get service health](https://learn.microsoft.com/en-us/graph/api/servicehealth-get?view=graph-rest-1.0) | [serviceHealth](https://learn.microsoft.com/en-us/graph/api/resources/servicehealth?view=graph-rest-1.0) | Retrieve the properties and relationships of a [serviceHealth](https://learn.microsoft.com/en-us/graph/api/resources/servicehealth?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The service ID. |
| service | String | The service name. Use the [list healthOverviews](https://learn.microsoft.com/en-us/graph/api/serviceannouncement-list-healthoverviews?view=graph-rest-1.0) operation to get exact string names for services subscribed by the tenant. |
| status | serviceHealthStatus | Show the overall service health status. The possible values are: `serviceOperational`, `investigating`, `restoringService`, `verifyingService`, `serviceRestored`, `postIncidentReviewPublished`, `serviceDegradation`, `serviceInterruption`, `extendedRecovery`, `falsePositive`, `investigationSuspended`, `resolved`, `mitigatedExternal`, `mitigated`, `resolvedExternal`, `confirmed`, `reported`, `unknownFutureValue`. For more information, see [serviceHealthStatus values](https://learn.microsoft.com/en-us/graph/api/resources/servicehealthissue?view=graph-rest-1.0#servicehealthstatus-values). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| issues | Collection\([serviceHealthIssue](https://learn.microsoft.com/en-us/graph/api/resources/servicehealthissue?view=graph-rest-1.0)\) | A collection of issues that happened on the service, with detailed information for each issue. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceHealth",
  "service": "String",
  "status": "String",
  "id": "String (identifier)"
}
```
