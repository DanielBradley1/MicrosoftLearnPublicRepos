<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# authenticationContextClassReference resource type

Namespace: microsoft.graph

Represents a Microsoft Entra authentication context class reference. Authentication context class references are custom values that define a Conditional Access authentication requirement. For more information, see [Developer guide to Conditional Access authentication context](https://learn.microsoft.com/en-us/entra/identity-platform/developer-guide-conditional-access-authentication-context).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-authenticationcontextclassreferences?view=graph-rest-1.0) | [authenticationContextClassReference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference?view=graph-rest-1.0) collection | Get all of the authenticationContextClassReference objects in the organization. |
| [Create or update](https://learn.microsoft.com/en-us/graph/api/authenticationcontextclassreference-update?view=graph-rest-1.0)\) | [authenticationContextClassReference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference?view=graph-rest-1.0) | Create or update an authenticationContextClassReference object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/authenticationcontextclassreference-get?view=graph-rest-1.0) | [authenticationContextClassReference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference?view=graph-rest-1.0) | Read properties and relationships of a authenticationContextClassReference object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authenticationcontextclassreference-delete?view=graph-rest-1.0) | [authenticationContextClassReference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference?view=graph-rest-1.0) | Delete an authenticationContextClassReference object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A short explanation of the policies that are enforced by authenticationContextClassReference. This value should be used to provide secondary text to describe the authentication context class reference when building user-facing admin experiences. For example, a selection UX. |
| displayName | String | The display name is the friendly name of the authenticationContextClassReference object. This value should be used to identify the authentication context class reference when building user-facing admin experiences. For example, a selection UX. |
| id | String | Identifier used to reference the authentication context class. The ID is used to trigger step-up authentication for the referenced authentication requirements and is the value that will be issued in the `acrs` claim of an access token. This value in the claim is used to verify that the required authentication context has been satisfied. The allowed values are `c1` through `c25`.  <br>Supports `$filter` \(`eq`\). |
| isAvailable | Boolean | Indicates whether the authenticationContextClassReference has been published by the security admin and is ready for use by apps. When it's set to `false`, it shouldn't be shown in authentication context selection UX, or used to protect app resources. It's shown and available for Conditional Access policy authoring. The default value is `false`.  <br>Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
    {
      "description": "String",
      "displayName": "String",
      "id": "String",
      "isAvailable": "Boolean",
    }
```
