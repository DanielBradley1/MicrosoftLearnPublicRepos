<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsDefinitionAuthorizationSystem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the authorization system that the permissions will be requested on.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorizationSystemId | String | ID of the [authorization system](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) retrieved from the customer cloud environment. |
| authorizationSystemType | String | The type of [authorization system](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsDefinitionAuthorizationSystem",
  "authorizationSystemId": "String",
  "authorizationSystemType": "String"
}
```
