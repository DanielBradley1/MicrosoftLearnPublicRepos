<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# tokenLifetimePolicy resource type

Namespace: microsoft.graph

Represents a policy that can control the lifetime of a JWT access token, an ID token or a SAML 1.1/2.0 token issued by Microsoft Entra ID. You can set token lifetimes for all apps in your organization, for a multitenant \(multi-organization\) application, or for a specific service principal in your organization. For more scenario details, see [Configurable token lifetimes in the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/configurable-token-lifetimes).

Configuring this policy for refresh tokens and session tokens isn't supported.

Inherits from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tokenlifetimepolicy-list?view=graph-rest-1.0) | [tokenLifetimePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy?view=graph-rest-1.0) | Read properties and relationships of tokenLifetimePolicies objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/tokenlifetimepolicy-post-tokenlifetimepolicies?view=graph-rest-1.0) | [tokenLifetimePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy?view=graph-rest-1.0) | Create a tokenLifetimePolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tokenlifetimepolicy-get?view=graph-rest-1.0) | [tokenLifetimePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy?view=graph-rest-1.0) | Read properties and relationships of a tokenLifetimePolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tokenlifetimepolicy-update?view=graph-rest-1.0) | None | Update a tokenLifetimePolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/tokenlifetimepolicy-delete?view=graph-rest-1.0) | None | Delete a tokenLifetimePolicy object. |
| [List applied to applications](https://learn.microsoft.com/en-us/graph/api/tokenlifetimepolicy-list-appliesto?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the list of directoryObjects that this policy has been applied to. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for this policy. For more information about the JSON schema for this property, see [Properties of a token lifetime policy definition](#properties-of-a-token-lifetime-policy-definition) . Required. |
| displayName | String | Display name for this policy. Required. |
| id | String | Unique identifier for this policy. Read-only. |
| isOrganizationDefault | Boolean | If set to `true`, activates this policy. There can be many policies for the same policy type, but only one can be activated as the organization default. Optional, default value is `false`. |

### Properties of a token lifetime policy definition

The following JSON object shows the properties in a token lifetime policy definition property. This JSON object must be **converted to a string with quotations escaped** to be inserted into the **definition** property as shown in the example.

```json
"definition": [
    "{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\"}}"
  ]
```

Note

All time durations in these properties are specified in the format "dd.hh:mm:ss". Maximum values for properties denoted in "days" are 1 second short of the denoted number of days. For example, the max value of 1 days is specified as "23:59:59".

| Property | Type | Description | Min Value | Max Value | Default Value |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AccessTokenLifetime | String | Controls how long both access and ID tokens are considered valid. | 10 minutes | 1 day | 1 hour |
| Version | Integer | Set value of 1. Required. | None | None | None |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection that this policy has been applied to. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "definition": ["String"],
  "displayName": "String",
  "id": "String (identifier)",
  "isOrganizationDefault": true,
}
```
