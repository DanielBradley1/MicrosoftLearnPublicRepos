<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# validatingDomains resource type

Namespace: microsoft.graph

Defines the types of domains to which the federated token validation applies. The **validatingDomains** property of the [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) resource uses this type.

This object is an abstract type from which the following resources derive:

- [allDomains](https://learn.microsoft.com/en-us/graph/api/resources/alldomains?view=graph-rest-1.0)
- [enumeratedDomains](https://learn.microsoft.com/en-us/graph/api/resources/enumerateddomains?view=graph-rest-1.0)

Note

As part of Microsoft's secure-by-default security posture, cross-domain federated sign-ins are blocked to reduce the risk of cross-realm impersonation. When **rootDomains** is configured to a value other than `none`, Microsoft Entra enforces domain-matching validation, ensuring that federated tokens are accepted only when the token issuer's domain aligns with the user's UPN domain or another explicitly configured validating domain.

Although Microsoft recommends maintaining domain-matching enforcement, administrators can intentionally configure a less restrictive policy if required.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rootDomains | [rootDomains](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#rootdomains-values) | Defines the types of domains to which the validation applies. The possible values are:  <br><br><br>- `none`: Disable cross-domain validation completely. No root-domain matching occurs. This is not the most secure option. Microsoft Entra ID doesn't verify that the sign-in domain matches an expected domain for authentication. As a result, organizations lose an additional layer of domain validation that can help detect configuration issues or unexpected identities. If a federated identity provider \(IdP\) is compromised or malicious, it can authenticate as users outside its intended domain scope, extending the impact from a single domain to potentially the entire tenant. Customers using this setting are encouraged to rely on controls such as MFA, Conditional Access, trusted identity providers, and application authorization policies to protect access.<br>- `all` \(default\): Requires a domain match for all domains; users are allowed to sign in only if their domain matches.<br>- `allFederated`: Blocks sign in if the user's domain is federated \(for example, when the user comes from a different federated domain\), but allows sign in if the user's domain is managed.<br>- `allManaged`: Blocks sign in if the user's domain is managed, but allows sign in for users from federated domains.<br>- `enumerated`: Blocks sign in if the user's domain is in the specified enumerated domains list.<br>- `allManagedAndEnumeratedFederated`: Blocks sign in for all managed domains, and blocks federated domains that are included in the enumerated domains list.<br>- `unknownFutureValue`: Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.validatingDomains",
  "rootDomains": "String"
}
```
