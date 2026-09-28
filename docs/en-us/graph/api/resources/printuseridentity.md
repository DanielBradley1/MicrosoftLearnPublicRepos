<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printuseridentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# printUserIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user identity within the Universal Print service. Maps to an [Microsoft Entra user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The printUserIdentity's identifier. Read-only. |
| displayName | String | The printUserIdentity's display name. |
| ipAddress | String | The printUserIdentity' IP address. Not populated. |
| userPrincipalName | String | The printUserIdentity's user principal name \(UPN\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "displayName": "String",
  "ipAddress": "String",
  "userPrincipalName": "String"
}
```
