<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-23 -->

# monitoring resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the entry point to access all resources related to alerts in the [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com).

The alert monitoring API provides a programmatic alert experience in the Microsoft Endpoint Manager admin center. A Microsoft Endpoint Manager admin can create an [alert rule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta) with preferred notification channels, and receive alerts when conditions set as thresholds in alert rules are met. Notification channels may include email and Microsoft Endpoint Manager admin center notifications. Each alert is recorded as an [alert record](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta). Admins can review alert records to learn about alert impact, severity, status, and more.

Admin roles such as Intune admins and Windows 365 admins have full access to the alert monitoring API.

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the alert. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alertRecords | [microsoft.graph.deviceManagement.alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) collection | The collection of records of alert events. |
| alertRules | [microsoft.graph.deviceManagement.alertRule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta) collection | The collection of alert rules. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.monitoring",
  "id": "String (identifier)"
}
```
