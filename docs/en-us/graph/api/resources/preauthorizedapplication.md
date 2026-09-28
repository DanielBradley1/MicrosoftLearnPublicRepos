<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/preauthorizedapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# preAuthorizedApplication resource type

Namespace: microsoft.graph

Lists the client applications that are preauthorized with the specified permissions to access this application's APIs. Users aren't required to consent to any preauthorized application \(for the permissions specified\). However, any other permissions not listed in preAuthorizedApplications \(requested through incremental consent for example\) require user consent.

In some rare cases, an identifier listed in the `delegatedPermissionIds` property may actually identify an [app role](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) \(from the service principal's `appRoles` property\), indicating that the client application identified by the `appId` property has been preauthorized for that app role.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The unique identifier for the application. |
| delegatedPermissionIds | String collection | The unique identifier for the [oauth2PermissionScopes](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) the application requires. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appId": "String",
  "delegatedPermissionIds": ["String"]
}
```
