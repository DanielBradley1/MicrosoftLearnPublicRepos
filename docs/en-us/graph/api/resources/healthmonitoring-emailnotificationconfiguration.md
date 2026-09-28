<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-emailnotificationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# emailNotificationConfiguration resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the email configuration for an alert type in Microsoft Entra Health monitoring.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupId | String | The identifier of the group to send an email to. All group types with configured email addresses are supported. |
| isEnabled | Boolean | Indicates whether email notifications are enabled on the alert type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.emailNotificationConfiguration",
  "groupId": "String",
  "isEnabled": "Boolean"
}
```
