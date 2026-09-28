<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/claimsmapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# claimsMapping resource type

Namespace: microsoft.graph

After the custom identity provider sends an ID token back to Azure AD B2C, Azure AD B2C maps the claims from a token to the claims that Azure AD B2C recognizes and uses.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The claim that provides the display name or full name for the user. Required. |
| email | String | The claim that provides the email address of the user. |
| givenName | String | The claim that provides the first name of the user. |
| surname | String | The claim that provides the last name of the user. |
| userId | String | The claim that provides the unique identifier for the signed-in user. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "email": "String",
  "givenName": "String",
  "surname": "String",
  "userId": "String"
  }
```
