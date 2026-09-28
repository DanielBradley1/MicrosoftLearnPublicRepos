<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-user?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# user resource type \(account in Microsoft Defender for Identity\)

Namespace: microsoft.graph.security

Represents details of a user identity account.

Inherits from [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accounts | [microsoft.graph.security.account](https://learn.microsoft.com/en-us/graph/api/resources/security-account?view=graph-rest-1.0) collection | Collection of accounts of the identity in different identity providers. Inherited from [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0). |
| cloudSecurityIdentifier | String | The cloud security identifier of the identity account. Inherited from [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0). |
| displayName | String | The display name of the identity account. Inherited from [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0). |
| domain | String | The domain name of the identity account. Inherited from [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0). |
| emailAddress | String | Email address of the user. |
| id | String | Unique identifier to represent the identity account. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| isEnabled | Boolean | Boolean indicating if the identity account is enabled. Inherited from [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0). |
| onPremisesSecurityIdentifier | String | The on-premises security identifier of the identity account. Inherited from [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0). |
| userPrincipalName | String | The user principal name. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.user",
  "id": "String (identifier)",
  "displayName": "String",
  "domain": "String",
  "onPremisesSecurityIdentifier": "String",
  "cloudSecurityIdentifier": "String",
  "isEnabled": "Boolean",
  "accounts": [
    {
      "@odata.type": "microsoft.graph.security.account"
    }
  ],
  "emailAddress": "String",
  "userPrincipalName": "String"
}
```
