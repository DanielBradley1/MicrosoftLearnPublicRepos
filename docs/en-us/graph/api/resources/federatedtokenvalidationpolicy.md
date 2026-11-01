<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# federatedTokenValidationPolicy resource type

Namespace: microsoft.graph

Represents a policy to control enabling or disabling validation of federation authentication tokens. It allows matching an on-premises federated account and a mapped Microsoft Entra ID account's root domain. When enabled, Microsoft Entra ID rejects an authentication request if the on-premises federated account and the mapped Microsoft Entra ID account's root domain don't match.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/federatedtokenvalidationpolicy-get?view=graph-rest-1.0) | [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) | Read the properties and relationships of a [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/federatedtokenvalidationpolicy-update?view=graph-rest-1.0) | [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) | Update the properties of a [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object wasn't deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| id | String | The unique identifier for the object. Key. Not nullable. Read-only. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| validatingDomains | [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-1.0) | Verified Microsoft Entra ID domains that Microsoft Entra ID validates that the federated account's root domain matches with the mapped Microsoft Entra account's root domain. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.federatedTokenValidationPolicy",
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)",
  "validatingDomains": {
    "@odata.type": "#microsoft.graph.validatingDomains",
    "rootDomains": "String"
  }
}
```
