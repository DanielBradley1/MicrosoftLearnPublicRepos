<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/optionalclaim?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# optionalClaim resource type

Namespace: microsoft.graph

Contains an optional claim associated with an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) . The `idToken`, `accessToken`, and `saml2Token` properties of the [optionalClaims](https://learn.microsoft.com/en-us/graph/api/resources/optionalclaims?view=graph-rest-1.0) resource is a collection of **optionalClaim**. If supported by a specific claim, you can also modify the behavior of the optionalClaim using the `additionalProperties` property.

For more information, see [provide optional claims to your Microsoft Entra app](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-optional-claims).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalProperties | String collection | Additional properties of the claim. If a property exists in this collection, it modifies the behavior of the optional claim specified in the name property. |
| essential | Boolean | If the value is true, the claim specified by the client is necessary to ensure a smooth authorization experience for the specific task requested by the end user. The default value is false. |
| name | String | The name of the optional claim. |
| source | String | The source \(directory object\) of the claim. There are predefined claims and user-defined claims from extension properties. If the source value is null, the claim is a predefined optional claim. If the source value is user, the value in the name property is the extension property from the user object. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "additionalProperties": ["String"],
  "essential": true,
  "name": "String",
  "source": "String"
}
```
