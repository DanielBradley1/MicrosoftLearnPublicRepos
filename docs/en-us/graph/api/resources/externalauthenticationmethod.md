<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# externalAuthenticationMethod resource type

Namespace: microsoft.graph

A representation of an external MFA registered to a user. External MFA is used to sign in to Microsoft Entra ID using an external identity provider.

The **externalAuthenticationMethod** resource is a derived type of the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-externalauthenticationmethods?view=graph-rest-1.0) | [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0) collection | Get a list of the externalAuthenticationMethod objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/authentication-post-externalauthenticationmethods?view=graph-rest-1.0) | [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0) | Create a new externalAuthenticationMethod object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalauthenticationmethod-get?view=graph-rest-1.0) | [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0) | Read the properties and relationships of an externalAuthenticationMethod object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authentication-delete-externalauthenticationmethods?view=graph-rest-1.0) | None | Delete an externalAuthenticationMethod object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configurationId | String | A unique identifier used to manage the external auth method within Microsoft Entra ID. |
| createdDateTime | DateTimeOffset | Represents the date and time when an entity was created. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| displayName | String | Custom name given to the registered external MFA. |
| id | String | The unique identifier for an the authentication method for the user. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalAuthenticationMethod",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "configurationId": "String",
  "displayName": "String"
}
```
