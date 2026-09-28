<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/adminappsandservices?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# adminAppsAndServices resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Company-wide configuration for apps and services.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/adminappsandservices-get?view=graph-rest-beta) | [adminAppsAndServices](https://learn.microsoft.com/en-us/graph/api/resources/adminappsandservices?view=graph-rest-beta) | Read the properties and relationships of a [adminAppsAndServices](https://learn.microsoft.com/en-us/graph/api/resources/adminappsandservices?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/adminappsandservices-update?view=graph-rest-beta) | [adminAppsAndServices](https://learn.microsoft.com/en-us/graph/api/resources/adminappsandservices?view=graph-rest-beta) | Update the properties and relationships of a [adminAppsAndServices](https://learn.microsoft.com/en-us/graph/api/resources/adminappsandservices?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique ID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| settings | [appsAndServicesSettings](https://learn.microsoft.com/en-us/graph/api/resources/appsandservicessettings?view=graph-rest-beta) | Company-wide settings for apps and services. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adminAppsAndServices",
  "id": "String (identifier)",
  "settings": {
    "@odata.type": "appsAndServicesSettings"
  }
}
```
