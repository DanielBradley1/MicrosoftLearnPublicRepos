<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appsandservicessettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# appsAndServicesSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Company-wide settings for apps and services. This object is configured in the **settings** property of [adminAppsAndServices](https://learn.microsoft.com/en-us/graph/api/resources/adminappsandservices?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isAppAndServicesTrialEnabled | Boolean | Controls whether users can start trial subscriptions for apps and services in your organization. |
| isOfficeStoreEnabled | Boolean | Controls whether users can access the Microsoft Store. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appsAndServicesSettings",
  "isOfficeStoreEnabled": "Boolean",
  "isAppAndServicesTrialEnabled": "Boolean"
}
```
