<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodsroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-02 -->

# authenticationMethodsRoot resource type

Namespace: microsoft.graph

Container for navigation properties of resources for Microsoft Entra authentication methods.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| userRegistrationDetails | [userRegistrationDetails](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationdetails?view=graph-rest-1.0) | Represents the state of a user's authentication methods, including which methods are registered and which features the user is registered and capable of \(such as multifactor authentication, self-service password reset, and passwordless authentication\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodsRoot",
  "id": "String (identifier)"
}
```
