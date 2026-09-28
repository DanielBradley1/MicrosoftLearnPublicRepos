<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# identityAccounts resource type

Namespace: microsoft.graph.security

Refers to any user or service account that is monitored for suspicious or malicious activity by Microsoft Defender for Identity within your identity infrastructure.

This resource is an abstract type from which the [microsoft.graph.security.user](https://learn.microsoft.com/en-us/graph/api/resources/security-user?view=graph-rest-1.0) is derived.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-identityaccounts?view=graph-rest-1.0) | [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0) collection | Get a list of the identity account objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-identityaccounts-get?view=graph-rest-1.0) | [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0) | Read the properties and relationships of a identity account object. |
| [invokeAction](https://learn.microsoft.com/en-us/graph/api/security-identityaccounts-invokeaction?view=graph-rest-1.0) | [microsoft.graph.security.invokeActionResult](https://learn.microsoft.com/en-us/graph/api/resources/security-invokeactionresult?view=graph-rest-1.0) | Invoke an action for the account. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accounts | [microsoft.graph.security.account](https://learn.microsoft.com/en-us/graph/api/resources/security-account?view=graph-rest-1.0) collection | Collection of accounts of the identity in different identity providers. |
| cloudSecurityIdentifier | String | The cloud security identifier of the identityAccount. |
| displayName | String | The Active Directory display name of the identityAccount. |
| domain | String | The Active Directory domain name of the identityAccount. |
| id | String | Unique identifier to represent the identity account. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| isEnabled | Boolean | Boolean indicating if the identityAccounts is enabled. |
| onPremisesSecurityIdentifier | String | The on-premises security identifier of the identityAccount. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.identityAccounts",
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
  ]
}
```
