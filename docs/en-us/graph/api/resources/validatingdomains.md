<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-23 -->

# validatingDomains resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the types of domains to which the federated token validation applies.

This object is an abstract type from which the following resources derive:

- [allDomains](https://learn.microsoft.com/en-us/graph/api/resources/alldomains?view=graph-rest-beta)
- [enumeratedDomains](https://learn.microsoft.com/en-us/graph/api/resources/enumerateddomains?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rootDomains | rootDomains | Defines the types of domains to which the validation applies. The possible values are:  <br><br><br>- `none`: Allows sign in without any domain match; this is the least secure option and is highly discouraged.<br>- `all`: Requires a domain match for all domains; users are allowed to sign in only if their domain matches.<br>- `allFederated`: Blocks sign in if the user's domain is federated \(for example, when the user comes from a different federated domain\), but allows sign in if the user's domain is managed.<br>- `allManaged`: Blocks sign in if the user's domain is managed, but allows sign in for users from federated domains.<br>- `enumerated`: Blocks sign in if the user's domain is in the specified enumerated domains list.<br>- `allManagedAndEnumeratedFederated`: Blocks sign in for all managed domains, and blocks federated domains that are included in the enumerated domains list.<br>- `unknownFutureValue`: Evolvable enumeration sentinel value. Don't use. |

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
