<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# alertConfiguration resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration of an alert type defining behavior that occurs when an alert is created in Microsoft Entra Health monitoring. For more information about alert configurations, see [What is Microsoft Entra Health?](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-microsoft-entra-health).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-healthmonitoringroot-list-alertconfigurations?view=graph-rest-beta) | [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alertconfiguration-get?view=graph-rest-beta) | [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alertconfiguration-update?view=graph-rest-beta) | [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) | Update the properties of a [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailNotificationConfigurations | [microsoft.graph.healthMonitoring.emailNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-emailnotificationconfiguration?view=graph-rest-beta) collection | Defines the recipients of email notifications for an alert type. Currently, only one email notification configuration is supported for an alert configuration, meaning only one group can receive notifications for an alert type. |
| id | String | The unique identifier of this alert configuration under the associated tenant. For example: `mfaSignInFailure`, `managedDeviceSignInFailure`. The possible values correspond to the values of **alertType** for an [alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) object. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.alertConfiguration",
  "id": "String (identifier)",
  "emailNotificationConfigurations": [
    {
      "@odata.type": "microsoft.graph.healthMonitoring.emailNotificationConfiguration"
    }
  ]
}
```
