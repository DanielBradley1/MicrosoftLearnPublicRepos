<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-21 -->

# preApprovedPermissions resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A **preApprovedPermissions** type describes the set of permissions that are pre-approved for the resource. The type is an abstract base type from which the following types are derived:

- [allPreApprovedPermissions](https://learn.microsoft.com/en-us/graph/api/resources/allpreapprovedpermissions?view=graph-rest-beta) indicates all permissions for all APIs are pre-approved
- [allPreApprovedPermissionsOnResourceApp](https://learn.microsoft.com/en-us/graph/api/resources/allpreapprovedpermissionsonresourceapp?view=graph-rest-beta) indicates all permissions for a specified API are pre-approved
- [enumeratedPreApprovedPermissions](https://learn.microsoft.com/en-us/graph/api/resources/enumeratedpreapprovedpermissions?view=graph-rest-beta) indicates that only the specified permissions have been pre-approved

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permissionKind | permissionKind | Indicates the scope of permissions that are included in this condition set. Possible values: `all` for all permissions, `enumerated` for a given list of permissions, or `allPermissionsOnResourceApp` for all permissions from a given API. Required. |
| permissionType | permissionType | The type of permission being granted. Possible values: `application` for application permissions, or `delegated` for delegated permissions. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.preApprovedPermissions",
  "permissionKind": "String",
  "permissionType": "String"
}
```
