<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-useraccount?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# userAccount resource type

Namespace: microsoft.graph.security

Represents common properties for a user account.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountName | String | The displayed name of the user account. |
| activeDirectoryObjectGuid | Guid | The unique user identifier assigned by the on-premises Active Directory. |
| azureAdUserId | String | The user object identifier in Microsoft Entra ID. |
| displayName | String | The user display name in Microsoft Entra ID. |
| domainName | String | The name of the Active Directory domain of which the user is a member. |
| resourceAccessEvents | [microsoft.graph.security.resourceAccessEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-resourceaccessevent?view=graph-rest-1.0) collection | Information on resource access attempts made by the user account. |
| tenantId | String | The Microsoft Entra tenant ID of the user account. |
| userPrincipalName | String | The user principal name of the account in Microsoft Entra ID. |
| userSid | String | The local security identifier of the user account. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.userAccount",
  "accountName": "String",
  "activeDirectoryObjectGuid": "Guid",
  "azureAdUserId": "String",
  "tenantId": "String",
  "displayName": "String",
  "domainName": "String",
  "resourceAccessEvents": [
	{
	  "@odata.type": "microsoft.graph.security.resourceAccessEvent"
	}
  ],
  "userPrincipalName": "String",
  "userSid": "String"
}
```
