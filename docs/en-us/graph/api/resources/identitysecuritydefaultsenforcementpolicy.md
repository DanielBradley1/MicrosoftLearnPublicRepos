<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitysecuritydefaultsenforcementpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# identitySecurityDefaultsEnforcementPolicy resource type

Namespace: microsoft.graph

Represents the Microsoft Entra ID [security defaults](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) policy. Security defaults contain preconfigured security settings that protect against common attacks.

Inherits from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitysecuritydefaultsenforcementpolicy-get?view=graph-rest-1.0) | [identitySecurityDefaultsEnforcementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitysecuritydefaultsenforcementpolicy?view=graph-rest-1.0) | Read the properties of an **identitySecurityDefaultsEnforcementPolicy** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identitysecuritydefaultsenforcementpolicy-update?view=graph-rest-1.0) | [identitySecurityDefaultsEnforcementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitysecuritydefaultsenforcementpolicy?view=graph-rest-1.0) | Update an **identitySecurityDefaultsEnforcementPolicy** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for this policy. Read-only. |
| displayName | String | Display name for this policy. Read-only. |
| id | String | Identifier for this policy. Read-only. |
| isEnabled | Boolean | If set to `true`, Microsoft Entra security defaults are enabled for the tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isEnabled": true
}
```
