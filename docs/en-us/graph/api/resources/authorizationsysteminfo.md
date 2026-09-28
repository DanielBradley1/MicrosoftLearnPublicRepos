<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorizationsysteminfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# authorizationSystemInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the authorization system's identifying information.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorizationSystemType | authorizationSystemType | The type of authorization system.The possible values are: `azure`, `gcp`, `aws`, `unknownFutureValue`. |
| displayName | String | Display name for the authorization system. |
| id | String | Unique identifier for the authorization system. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authorizationSystemInfo",
  "id": "String",
  "displayName": "String",
  "authorizationSystemType": "String"
}
```
