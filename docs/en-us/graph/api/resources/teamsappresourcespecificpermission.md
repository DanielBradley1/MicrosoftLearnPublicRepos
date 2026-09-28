<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappresourcespecificpermission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamsAppResourceSpecificPermission resource type

Namespace: microsoft.graph

Represents the resource-specific permission associated with a **teamsApp**.

For details, see [understanding resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permissionType | [teamsAppResourceSpecificPermissionType](https://learn.microsoft.com/en-us/graph/api/resources/teamsappresourcespecificpermission?view=graph-rest-1.0#teamsappresourcespecificpermissiontype-values) | The type of resource-specific permission. |
| permissionValue | String | The name of the resource-specific permission. |

## teamsAppResourceSpecificPermissionType values

| Member | Description |
| :--- | :--- |
| delegated | Indicates that the resource specific permission is of delegated type. |
| application | Indicates that the resource specific permission is of application type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppResourceSpecificPermission",
  "permissionValue": "String",
  "permissionType": "String"
}
```
