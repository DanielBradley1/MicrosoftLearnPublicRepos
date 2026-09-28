<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedpermissionclassification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# delegatedPermissionClassification resource type

Namespace: microsoft.graph

Specifies the classification of a delegated permission.

Delegated permission classifications can be used in combination with user consent settings to choose which permissions a user is allowed to consent to. See [Configure how end-users consent to applications](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-user-consent) to learn more about permission classifications.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| classification | permissionClassificationType | The classification value. Possible values: `low`, `medium` \(preview\), `high` \(preview\). Doesn't support `$filter`. |
| id | String | A unique identifier for the **delegatedPermissionClassification** Key. Not nullable. Read-only. |
| permissionId | String | The unique identifier \(**id**\) for the delegated permission listed in the **oauth2PermissionScopes** collection of the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). Required on create. Doesn't support `$filter`. |
| permissionName | String | The claim value \(**value**\) for the delegated permission listed in the **oauth2PermissionScopes** collection of the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). Doesn't support `$filter`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "classification": "low",
  "id": "String (identifier)",
  "permissionId": "String",
  "permissionName": "String"
}
```
