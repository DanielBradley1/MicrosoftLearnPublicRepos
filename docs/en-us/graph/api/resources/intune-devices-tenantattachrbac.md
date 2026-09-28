<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-tenantattachrbac?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# tenantAttachRBAC resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for tenant attach enablement functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get tenantAttachRBAC](https://learn.microsoft.com/en-us/graph/api/intune-devices-tenantattachrbac-get?view=graph-rest-beta) | [tenantAttachRBAC](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-tenantattachrbac?view=graph-rest-beta) | Read properties and relationships of the [tenantAttachRBAC](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-tenantattachrbac?view=graph-rest-beta) object. |
| [Update tenantAttachRBAC](https://learn.microsoft.com/en-us/graph/api/intune-devices-tenantattachrbac-update?view=graph-rest-beta) | [tenantAttachRBAC](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-tenantattachrbac?view=graph-rest-beta) | Update the properties of a [tenantAttachRBAC](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-tenantattachrbac?view=graph-rest-beta) object. |
| [enable action](https://learn.microsoft.com/en-us/graph/api/intune-devices-tenantattachrbac-enable?view=graph-rest-beta) | None |  |
| [getState function](https://learn.microsoft.com/en-us/graph/api/intune-devices-tenantattachrbac-getstate?view=graph-rest-beta) | [tenantAttachRBACState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-tenantattachrbacstate?view=graph-rest-beta) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this entity |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.tenantAttachRBAC",
  "id": "String (identifier)"
}
```
