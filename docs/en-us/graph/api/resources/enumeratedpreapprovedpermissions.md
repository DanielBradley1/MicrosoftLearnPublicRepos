<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enumeratedpreapprovedpermissions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# enumeratedPreApprovedPermissions resource type

Namespace: microsoft.graph.enumeratedPreApprovedPermissions

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This type is used in the conditions of a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) to indicate that only the permissions explicitly included in the policy are allowed for consent. If the client application requests more permissions after the policy is created, the policy will not apply.

Inherits from [preApprovePermissions](https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permissionIds | String collection | The list of **id** values for the specific resource-specific application permissions to match with. See the **resourceSpecificApplicationPermissions** property of the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta) object for the list of permissions. |
| permissionKind | permissionKind | Inherited from [preapprovedpermissions](https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta). Indicates the scope of permissions that are included in this condition set. Only `enumerated` is supported to indicate that only a selected set of permissions from a single resource application are allowed. Required. |
| permissionType | permissionType | The type of permission being granted. Possible values: `application` for application permissions \(app roles\), or `delegated` for delegated permissions. Inherited from [preapprovedpermissions](https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta). Required. |
| resourceApplicationId | String | The **appId** of the resource application \(the API\). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enumeratedPreApprovedPermissions",
  "permissionKind": "String",
  "permissionType": "String",
  "permissionIds": [
    "String"
  ],
  "resourceApplicationId": "String"
}
```
