<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-19 -->

# claimsMappingPolicy resource type

Namespace: microsoft.graph

Represents the claim-mapping policies for WS-Fed, SAML, OAuth 2.0, and OpenID Connect protocols, for tokens issued to a specific application. You can use claims-mapping policies to:

- Select which claims are included in tokens
- Create claim types that don't already exist
- Choose or change the source of data emitted in specific claims

The number of claims and transformations that can be added to a claims-mapping policy are limited to reduce token size. Any claims schema entries or transformations that are encountered after reaching the limit are ignored and not included in the issued token. For more information about the limits, see [Properties of a claims-mapping policy definition](#properties-of-a-claims-mapping-policy-definition).

Inherits from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-1.0).

For more scenarios and configuration details, see the following articles:

- [Customize claims emitted in tokens for a specific app in a tenant through the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity-platform/saml-claims-customization).
- [How to: Customize claims with the claims mapping policy in Microsoft Graph](https://learn.microsoft.com/en-us/graph/how-to-claims-customization).
- [Claims customization using a policy](https://learn.microsoft.com/en-us/entra/identity-platform/reference-claims-customization) to learn the difference between this policy and the [custom claims policy \(preview\)](https://learn.microsoft.com/en-us/graph/api/resources/customclaimspolicy).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/claimsmappingpolicy-list?view=graph-rest-1.0) | [claimsMappingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0) | Read properties and relationships of claimsMappingPolicies objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/claimsmappingpolicy-post-claimsmappingpolicies?view=graph-rest-1.0) | [claimsMappingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0) | Create a claimsMappingPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/claimsmappingpolicy-get?view=graph-rest-1.0) | [claimsMappingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0) | Read properties and relationships of a claimsMappingPolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/claimsmappingpolicy-update?view=graph-rest-1.0) | None | Update a claimsMappingPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/claimsmappingpolicy-delete?view=graph-rest-1.0) | None | Delete a claimsMappingPolicy object. |
| [List applies to](https://learn.microsoft.com/en-us/graph/api/claimsmappingpolicy-list-appliesto?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the list of directoryObjects to which this policy applies. |
| [Assign to service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-claimsmappingpolicies?view=graph-rest-1.0) | None | Assign a claimsMappingPolicy to a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object. |
| [List assigned to service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-claimsmappingpolicies?view=graph-rest-1.0) | [claimsMappingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0) collection | List the claimsMappingPolicy objects that are assigned to a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object. |
| [Unassign from service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-claimsmappingpolicies?view=graph-rest-1.0) | None | Remove a claimsMappingPolicy from a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for this policy. For more information about the JSON schema for this property, see [Properties of a claims-mapping policy definition](#properties-of-a-claims-mapping-policy-definition). Required. |
| displayName | String | Display name for this policy. Required. |
| id | String | Unique identifier for this policy. Read-only. |
| isOrganizationDefault | Boolean | Ignore this property. The claims-mapping policy can only be applied to service principals and can't be set globally for the organization. |

### Properties of a claims-mapping policy definition

The JSON object to be inserted into the **definition** property must first be **converted to a string with quotations escaped**. This section shows a few definition examples.

#### Example: **definition** to include the EmployeeID and TenantCountry as claims in tokens

```json
{
    "definition": [
        "{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\": [{\"Source\":\"user\",\"ID\":\"employeeid\",\"SamlClaimType\":\"http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name\",\"JwtClaimType\":\"name\"},{\"Source\":\"company\",\"ID\":\"tenantcountry\",\"SamlClaimType\":\"http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country\",\"JwtClaimType\":\"country\"}]}}"
    ],
    "displayName": "Test1234"
}
```

#### Example: **definition** that uses a claims transformation

```json
{
    "definition": [
        "{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\": [{\"Source\":\"user\",\"ID\":\"userprincipalname\",\"SamlClaimType\":\"http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier\"},{\"Source\":\"user\",\"ID\":\"givenname\",\"SamlClaimType\":\"http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname\"},{\"Source\":\"user\",\"ID\":\"displayname\",\"SamlClaimType\":\"http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name\"},{\"Source\":\"user\",\"ID\":\"surname\",\"SamlClaimType\":\"http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname\"},{\"Source\":\"user\",\"ID\":\"userprincipalname\",\"SamlClaimType\":\"username\"}],\"ClaimsTransformation\":[{\"ID\":\"CreateTermsOfService\",\"TransformationMethod\":\"CreateStringClaim\",\"InputParameters\": [{\"ID\":\"value\",\"DataType\":\"string\", \"Value\":\"sandbox\"}],\"OutputClaims\":[{\"ClaimTypeReferenceId\":\"TOS\",\"TransformationClaimType\":\"createdClaim\"}]}]}}"
    ],
    "displayName": "Test1234"
}
```

| Property | Type | Description |
| :--- | :--- | :--- |
| ClaimsSchema | JSON object | Defines which claims are present in the tokens affected by the policy, in addition to the basic claim set and the core claim set. For each claim schema entry defined in this property, certain information is required. Specify where the data is coming from \(Value or Source/ID pair\), and which claim the data is emitted as \(Claim Type\). A maximum of 50 claims are included in the token through the ClaimsSchema object. Any claims schema entries that are encountered after reaching the limit are ignored and don't appear in the issued token. Further details are available in the [ClaimsSchema definition](https://learn.microsoft.com/en-us/entra/identity-platform/saml-claims-customization) and [Properties of the policy used for claims customization](https://learn.microsoft.com/en-us/entra/identity-platform/reference-claims-customization#properties-of-the-policy-used-for-claims-customization). |
| ClaimsTransformation | JSON object | Defines common transformations that can be applied to source data, to generate the output data for claims specified in the ClaimsSchema. A maximum of 50 transformations are included in the token through the ClaimsTransformation object. Any transformations that are encountered after reaching the limit are ignored and don't appear in the issued token. For more information about ClaimsTransformation and the supported functions, see [Claims transformation](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-claims-mapping#claims-transformation). |
| IncludeBasicClaimSet | Boolean | If set to `true`, all claims in the basic claim set are emitted in tokens affected by the policy. If set to `false`, claims in the basic claim set aren't in the tokens, unless they're individually added in the ClaimsSchema property of the same policy. |
| Version | Integer | Set value of 1. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection to which this policy applies. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "definition": ["String"],
  "displayName": "String",
  "id": "String (identifier)",
  "isOrganizationDefault": false,
}
```
