<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# b2bManagementPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents Microsoft Entra B2B features in Microsoft Entra External ID for workforce tenants, including restricting/allowing which domains can be used to invite users, if auto redemption of invitations is allowed, and opt in of preview features.

Inherits from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/policyroot-list-b2bmanagementpolicies?view=graph-rest-beta) | [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) collection | Get a list of the b2bManagementPolicy objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/policyroot-post-b2bmanagementpolicies?view=graph-rest-beta) | [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) | Create a new b2bManagementPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/b2bmanagementpolicy-get?view=graph-rest-beta) | [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) | Read the properties and relationships of [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/b2bmanagementpolicy-update?view=graph-rest-beta) | [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) | Update the properties of a b2bManagementPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/policyroot-delete-b2bmanagementpolicies?view=graph-rest-beta) | None | Delete a b2bManagementPolicy object. |
| [List appliesTo](https://learn.microsoft.com/en-us/graph/api/b2bmanagementpolicy-list-appliesto?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Get the list of directoryObjects that this policy is applied to. |
| [Add appliesTo](https://learn.microsoft.com/en-us/graph/api/b2bmanagementpolicy-post-appliesto?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Add appliesTo by posting to the appliesTo collection. |
| [Remove appliesTo](https://learn.microsoft.com/en-us/graph/api/b2bmanagementpolicy-delete-appliesto?view=graph-rest-beta) | None | Remove a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) object that this policy is applied to. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and Time when the policy object was deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for a policy. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). Required. |
| description | String | Description for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). Required. |
| displayName | String | Display name for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). Required. |
| id | String | The unique identifier for the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isOrganizationDefault | Boolean | If set to true, activates this policy. There can be many policies for the same policy type, but only one can be activated as the organization default. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). Optional. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | The directoryObject collection that this policy is applied to. Read-only. Inherited from [microsoft.graph.stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2bManagementPolicy",
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
