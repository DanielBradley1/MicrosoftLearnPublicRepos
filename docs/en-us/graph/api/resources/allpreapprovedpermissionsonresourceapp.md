<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/allpreapprovedpermissionsonresourceapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# allPreApprovedPermissionsOnResourceApp resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This type is used in the conditions of a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) to indicate that only permissions on the resource app \(API\) specified in the policy are pre-approved for consent.

Inherits from [preApprovePermissions](https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permissionKind | permissionKind | Inherited from [preapprovedpermissions](https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta). Indicates the scope of permissions that are included in this condition set. Possible values: `all` for all permissions, `enumerated` for a given list of permissions, or `allPermissionsOnResourceApp` for all permissions from a given API. Only `allPermissionsOnResourceApp` is supported for the \*\*allPreApprovedPermissionsOnResourceApp \*\* object type. Required. |
| permissionType | permissionType | The type of permission being granted. Possible values: `application` for application permissions \(app roles\), or `delegated` for delegated permissions. Inherited from [preapprovedpermissions](https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta). Required. |
| resourceApplicationId | String | The **appId** of the resource application \(the API\). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.allPreApprovedPermissionsOnResourceApp",
  "permissionKind": "allPermissionsOnResourceApp",
  "permissionType": "String",
  "resourceApplicationId": "String"
}
```
