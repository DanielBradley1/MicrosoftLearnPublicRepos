<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolemanagement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# roleManagement resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get roleManagement](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolemanagement-get?view=graph-rest-beta) | [roleManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolemanagement?view=graph-rest-beta) | Read properties and relationships of the [roleManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolemanagement?view=graph-rest-beta) object. |
| [Update roleManagement](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolemanagement-update?view=graph-rest-beta) | [roleManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolemanagement?view=graph-rest-beta) | Update the properties of a [roleManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolemanagement?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceManagement | [rbacApplicationMultiple](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rbacapplicationmultiple?view=graph-rest-beta) | The RbacApplication for Device Management |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.roleManagement",
  "id": "String (identifier)"
}
```
