<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremauthenticationpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# onPremAuthenticationPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a policy that controls how authentication requests from on-premises environments are managed. This resource allows administrators to define and enforce rules for on-premises authentication scenarios for users and applications.

Inherits from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/policyroot-list-onpremauthenticationpolicies?view=graph-rest-beta) | [onPremAuthenticationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onpremauthenticationpolicy?view=graph-rest-beta) collection | Get a list of the onPremAuthenticationPolicy objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/policyroot-post-onpremauthenticationpolicies?view=graph-rest-beta) | [onPremAuthenticationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onpremauthenticationpolicy?view=graph-rest-beta) | Create a new onPremAuthenticationPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/onpremauthenticationpolicy-get?view=graph-rest-beta) | [onPremAuthenticationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onpremauthenticationpolicy?view=graph-rest-beta) | Read the properties and relationships of [onPremAuthenticationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onpremauthenticationpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/onpremauthenticationpolicy-update?view=graph-rest-beta) | [onPremAuthenticationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onpremauthenticationpolicy?view=graph-rest-beta) | Update the properties of an onPremAuthenticationPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/onpremauthenticationpolicy-delete?view=graph-rest-beta) | None | Delete an onPremAuthenticationPolicy object. |
| [List applies to](https://learn.microsoft.com/en-us/graph/api/onpremauthenticationpolicy-list-appliesto?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Get the list of directoryObjects that this policy has been applied to. |
| [Assign to](https://learn.microsoft.com/en-us/graph/api/onpremauthenticationpolicy-post-appliesto?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Add appliesTo by posting to the appliesTo collection. |
| [Remove applies to](https://learn.microsoft.com/en-us/graph/api/onpremauthenticationpolicy-delete-appliesto?view=graph-rest-beta) | None | Remove a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object isn't deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). Optional. |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for this policy. See below for more details about the JSON schema for this property. Required. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). |
| description | String | Description for this policy. Required. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). |
| displayName | String | Display name for this policy. Required. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). |
| id | String | Unique identifier for this policy. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isOrganizationDefault | Boolean | If set to true, this instance of the policy will be considered the default for the organization. There can be many policies for the same policy type, but only one can be activated as the organization default. Optional, default value is false. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | The [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection that this policy has been applied to. Read-only. Inherited from [microsoft.graph.stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPremAuthenticationPolicy",
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "definition": [
    "String"
  ],
  "isOrganizationDefault": "Boolean"
}
```
