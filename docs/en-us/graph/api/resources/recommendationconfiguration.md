<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recommendationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# recommendationConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration for recommendation notifications. This resource type is used to manage the notification settings for recommendations in Microsoft Entra ID. It allows you to enable or disable notifications for recommendations, which can help organizations stay informed about important security and compliance issues.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/recommendationconfiguration-get?view=graph-rest-beta) | [recommendationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/recommendationconfiguration?view=graph-rest-beta) | Read the properties of a recommendationConfiguration object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/recommendationconfiguration-update?view=graph-rest-beta) | None | Update the properties of a recommendationConfiguration object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isNotificationEnabled | Boolean | Indicates whether notifications for recommendations are enabled. |
| lastRefreshedDateTime | DateTimeOffset | The date and time of the most recent refresh cycle in which every pipeline that populates Microsoft Entra recommendations completed successfully for the tenant's region. The value advances only when all contributing pipelines succeed and remains at the last fully successful cycle if any contributing pipeline is unhealthy. A successful refresh doesn't imply that any individual recommendation changed. Is `null` when no fully successful refresh has been recorded yet. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.recommendationConfiguration",
  "isNotificationEnabled": "Boolean",
  "lastRefreshedDateTime": "String (timestamp)"
}
```
