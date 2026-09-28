<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-14 -->

# teamsAppSettings resource type

Namespace: microsoft.graph

Represents tenant-wide settings for all [Teams apps](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the tenant.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamsappsettings-get?view=graph-rest-1.0) | [teamsAppSettings](https://learn.microsoft.com/en-us/graph/api/resources/teamsappsettings?view=graph-rest-1.0) | Get the tenant-wide settings for all Teams apps in the tenant. |
| [Update](https://learn.microsoft.com/en-us/graph/api/teamsappsettings-update?view=graph-rest-1.0) | [teamsAppSettings](https://learn.microsoft.com/en-us/graph/api/resources/teamsappsettings?view=graph-rest-1.0) | Update the tenant-wide settings for all Teams apps in the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowUserRequestsForAppAccess | Boolean | Indicates whether users are allowed to request access to the unavailable Teams apps. |
| id | String | Unique identifier for the **teamsAppSettings** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isUserPersonalScopeResourceSpecificConsentEnabled | Boolean | Indicates whether resource-specific consent for personal scope in Teams apps is enabled for the tenant. `True` indicates that Teams apps that are allowed in the tenant and require resource-specific permissions can be installed in the personal scope. `False` blocks the installation of any Teams app that requires resource-specific permissions in the personal scope. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppSettings",
  "allowUserRequestsForAppAccess": "Boolean",
  "id": "String (identifier)",
  "isUserPersonalScopeResourceSpecificConsentEnabled": "Boolean"
}
```

## Related content

- [Resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent)
