<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# agentIdentity resource type

Namespace: microsoft.graph

Represents an agent identity in Microsoft Entra ID. An agent identity is an account used by AI agents to authenticate within the Microsoft Entra ID ecosystem.

Inherits from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0).

This resource is an open type that allows additional properties beyond those documented here.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentidentity-list?view=graph-rest-1.0) | [agentidentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) collection | Get a list of the agentidentity objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/agentidentity-post?view=graph-rest-1.0) | [agentidentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) | Create a new agentidentity object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentidentity-get?view=graph-rest-1.0) | [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) | Read the properties and relationships of [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentidentity-update?view=graph-rest-1.0) | [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) | Update the properties of an agentIdentity object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/agentidentity-delete?view=graph-rest-1.0) | None | Delete an agentIdentity object. |
| **App role assignments** |  |  |
| [List appRoleAssignedTo](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignedto?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the users, groups, and agent identities assigned app roles for this agent identity. |
| [List appRoleAssignments](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the app roles that this agent identity is assigned. |
| [Create appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Create a new appRoleAssignment object. |
| [Delete appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Delete an existing appRoleAssignment object. |
| **Delegated permission grants** |  |  |
| [List oauth2PermissionGrants](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-oauth2permissiongrants?view=graph-rest-1.0) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) collection | Get the delegated permission grants authorizing this agent identity to access an API on behalf of a signed-in user. |
| **Deleted items** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of recently deleted agent identities. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Retrieve the properties of a recently deleted agent identity. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Restore a recently deleted agent identity. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | None | Permanently delete an agent identity. |
| **Directory objects** |  |  |
| [List ownedObjects](https://learn.microsoft.com/en-us/graph/api/agentidentity-list-ownedobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get directory objects owned by this agent identity. |
| **Memberships** |  |  |
| [List direct memberships](https://learn.microsoft.com/en-us/graph/api/agentidentity-list-memberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups that this agent identity is a direct member of. |
| [List transitive memberships](https://learn.microsoft.com/en-us/graph/api/agentidentity-list-transitivememberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups that this agent identity is a member of. This operation is transitive and includes the groups that this agent identity is a nested member of. |
| **Owners** |  |  |
| [List owners](https://learn.microsoft.com/en-us/graph/api/agentidentity-list-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the owners of this agent identity. |
| [Add owners](https://learn.microsoft.com/en-us/graph/api/agentidentity-post-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add owners by posting to the owners collection. |
| [Remove owners](https://learn.microsoft.com/en-us/graph/api/agentidentity-delete-owners?view=graph-rest-1.0) | None | Remove a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) object. |
| **Sponsors** |  |  |
| [List sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentity-list-sponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the sponsors for this agent identity. |
| [Add sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentity-post-sponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add sponsors by posting to the sponsors collection. |
| [Remove sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentity-delete-sponsors?view=graph-rest-1.0) | None | Remove a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) object. |

## Properties

Important

While this resource inherits from **servicePrincipal**, some properties are not applicable.

| Property | Type | Description |
| :--- | :--- | :--- |
| odata.type | String | `#microsoft.graph.agentIdentity`. Distinguishes this object as an agent identity. Can be used to identify this object as an agent identity, instead of another kind of service principal. |
| accountEnabled | Boolean | `true` if the agent identity account is enabled; otherwise, `false`. If set to `false`, then no users are able to sign in to this app, even if they're assigned to it. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| agentIdentityBlueprintId | String | The **appId** of the agent identity blueprint that defines the configuration for this agent identity. |
| customSecurityAttributes | [customSecurityAttributeValue](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributevalue?view=graph-rest-1.0) | An open complex type that holds the value of a custom security attribute that is assigned to a directory object. Nullable. Requires `$select` to retrieve. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| createdByAppId | String | The **appId** of the application that created this agent identity. Set internally by Microsoft Entra ID. Read-only. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the agent identity was created. Read-only. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| disabledByMicrosoftStatus | String | Specifies whether Microsoft has disabled the registered Agent Identity Blueprint. The possible values are: `null` \(default value\), `NotDisabled`, and `DisabledDueToViolationOfServicesAgreement` \(reasons may include suspicious, abusive, or malicious activity, or a violation of the Microsoft Services Agreement\). Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| displayName | String | The display name for the agent identity. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| id | String | The unique identifier for the agent identity. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). Key. Not nullable. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| managerApplications | Guid collection | The collection of application IDs designated as managers of this agent identity's backing [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0). Read-only; the value is server-managed and reflects the **managerApplications** of the backing agentIdentityBlueprint. To change the managers, an owner or administrator must update the **managerApplications** property on the backing agentIdentityBlueprint **in the tenant where it's registered**. For multitenant agent identity blueprints, admins in a tenant where the blueprint is only consumed can't make this change — they must ask an owner or administrator in the blueprint's home tenant. Not nullable. Returned only on `$select`. |
| servicePrincipalType | String | Set to **ServiceIdentity** for all agent identities. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| tags | String collection | Custom strings that can be used to categorize and identify the agent identity. Not nullable. The value is the union of strings set here and on the associated Agent Identity Blueprint entity's **tags** property. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appRoleAssignedTo | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | App role assignments for this app or service, granted to users, groups, and other agent identities. Supports `$expand`. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| appRoleAssignments | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | App role assignment for another app or service, granted to this agent identity. Supports `$expand`. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| createdObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects created by this agent identity. Read-only. Nullable. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| memberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Roles that this agent identity is a member of. HTTP Methods: GET Read-only. Nullable. Supports `$expand`. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| oauth2PermissionGrants | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) collection | Delegated permission grants authorizing this agent identity to access an API on behalf of a signed-in user. Read-only. Nullable. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| ownedObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects that are owned by this agent identity. Read-only. Nullable. Supports `$expand` and `$filter` \(`/$count eq 0`, `/$count ne 0`, `/$count eq 1`, `/$count ne 1`\). Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| owners | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects that are owners of this agent identity. The owners are a set of nonadmin users or agent identities who are allowed to modify this object. Supports `$expand` and `$filter` \(`/$count eq 0`, `/$count ne 0`, `/$count eq 1`, `/$count ne 1`\). Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| sponsors | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The sponsors for this agent identity. |

## JSON representation

The following JSON representation shows the resource type. Only a subset of all properties are returned by default. All other properties can only be retrieved using $select.

```json
{
  "@odata.type": "#microsoft.graph.agentIdentity",
  "id": "String (identifier)",
  "accountEnabled": "Boolean",
  "agentIdentityBlueprintId": "String",
  "createdByAppId": "String",
  "createdDateTime": "String (timestamp)",
  "disabledByMicrosoftStatus": "String",
  "displayName": "String",
  "managerApplications": [
    "Guid"
  ],
  "servicePrincipalType": "String",
  "tags": [
    "String"
  ]
}
```
