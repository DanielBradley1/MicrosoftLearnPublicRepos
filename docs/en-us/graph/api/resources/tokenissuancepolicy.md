<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# tokenIssuancePolicy resource type

Namespace: microsoft.graph

Represents the policy to specify the characteristics of SAML tokens issued by Microsoft Entra ID. You can use token-issuance policies to:

- Set signing options
- Set signing algorithm
- Set SAML token version

Inherits from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tokenissuancepolicy-list?view=graph-rest-1.0) | [tokenIssuancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0) | Read properties and relationships of tokenIssuancePolicy objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/tokenissuancepolicy-post-tokenissuancepolicy?view=graph-rest-1.0) | [tokenIssuancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0) | Create a tokenIssuancePolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tokenissuancepolicy-get?view=graph-rest-1.0) | [tokenIssuancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0) | Read properties and relationships of a tokenIssuancePolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tokenissuancepolicy-update?view=graph-rest-1.0) | None | Update a tokenIssuancePolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/tokenissuancepolicy-delete?view=graph-rest-1.0) | None | Delete a tokenIssuancePolicy object. |
| [List applied to applications](https://learn.microsoft.com/en-us/graph/api/tokenissuancepolicy-list-appliesto?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the list of directoryObjects that this policy has been applied to. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for this policy. See below for more details about the JSON schema for this property. Required. |
| description | String | Description for this policy. |
| displayName | String | Display name for this policy. Required. |
| id | String | Unique identifier for this policy. Read-only. |
| isOrganizationDefault | Boolean | Ignore this property. The token-issuance policy can only be applied to service principals and can't be set globally for the organization. |

### Properties of a token issuance policy definition

The properties form the JSON object that represents a token issuance policy. This JSON object must be **converted to a string with quotations escaped** to be inserted into the **definition** property. The following is an example in JSON format:

```json
"definition": [
    "{ \"TokenIssuancePolicy\":{\"TokenResponseSigningPolicy\":\"TokenOnly\",\"SamlTokenVersion\":\"1.1\",\"SigningAlgorithm\":\"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256\",\"Version\":\"1\",\"EmitSAMLNameFormat\": \"true\"}}"
  ]
```

| Property | Type | Description |
| :--- | :--- | :--- |
| EmitSamlNameFormat | Boolean | If selected, Microsoft Entra ID will add an additional attribute called "NameFormat" that describes the format of the name to restricted, core, and optional claims for this application. [Learn more](https://learn.microsoft.com/en-us/azure/active-directory/develop/reference-claims-mapping-policy-type#claim-sets) |
| SamlTokenVersion | String | Version of the SAML token. Supported values are: `1.1`, `2.0`. |
| SigningAlgorithm | String | Signing algorithm use by Microsoft Entra ID to sign the SAML token. Supported values are: `http://www.w3.org/2001/04/xmldsig-more#rsa-sha256`, `http://www.w3.org/2000/09/xmldsig#rsa-sha1`. |
| Version | Integer | Set value of 1. Required. |
| TokenResponseSigningPolicy | String | Represents the certificate signing options available in Microsoft Entra ID. Supported values are: `ResponseOnly`, `TokenOnly`, `ResponseAndToken`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection that this policy has been applied to. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "definition": ["String"],
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isOrganizationDefault": true,
}
```
