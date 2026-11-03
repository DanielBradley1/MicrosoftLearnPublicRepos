<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# federatedTokenValidationPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a policy to control enabling or disabling validation of federation authentication tokens. It allows matching an on-premises federated account and a mapped Microsoft Entra ID account's root domain. When enabled, Microsoft Entra ID rejects an authentication request if the on-premises federated account and the mapped Microsoft Entra ID account's root domain don't match.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/policyroot-list-federatedtokenvalidationpolicy?view=graph-rest-beta) | [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta) collection | Get a list of the [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/federatedtokenvalidationpolicy-get?view=graph-rest-beta) | [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta) | Read the properties and relationships of a [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/federatedtokenvalidationpolicy-update?view=graph-rest-beta) | [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta) | Update the properties of a [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object wasn't deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| ID | String | The unique identifier for the object. Key. Not nullable. Read-only. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| validatingDomains | [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-beta) | Verified Microsoft Entra ID domains that Microsoft Entra ID validates that the federated account's root domain matches with the mapped Microsoft Entra account's root domain. |

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
    "@odata.type": "microsoft.graph.validatingDomains"
  }
}
```
