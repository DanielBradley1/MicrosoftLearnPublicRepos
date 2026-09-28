<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/audituseridentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# auditUserIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An open type that represents details of the identity of a user along with information about their home tenant.

Inherits from [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The user's display name. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta). |
| homeTenantId | String | For user sign ins, the identifier of the tenant that the user is a member of. |
| homeTenantName | String | For user sign ins, the name of the tenant that the user is a member of. Only populated in cases where the home tenant has provided affirmative consent to Microsoft Entra ID to show the tenant content. |
| id | String | The user's unique identifier. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta). |
| ipAddress | String | The IP address Microsoft Entra ID detected for the user's client. Inherited from [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta). |
| userPrincipalName | String | The user's User Principal Name \(UPN\). Inherited from [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.auditUserIdentity",
  "displayName": "String",
  "id": "String (identifier)",
  "ipAddress": "String",
  "userPrincipalName": "String",
  "homeTenantId": "String",
  "homeTenantName": "String"
}
```
