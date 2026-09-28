<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# agentIdentityBlueprintPrincipal resource type

Namespace: microsoft.graph

Represents an agent identity blueprint principal in a tenant. An agent identity blueprint principal is instantiated from an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object and is used to create [agent identities](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) within a Microsoft Entra ID tenant, and perform various identity management operations that affect all agent identities created.

Inherits from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0).

This resource is an open type that allows additional properties beyond those documented here.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-list?view=graph-rest-1.0) | [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) collection | Get a list of the agentIdentityBlueprintPrincipal objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-post?view=graph-rest-1.0) | [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) | Create a new agentIdentityBlueprintPrincipal object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-get?view=graph-rest-1.0) | [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) | Read the properties and relationships of [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-update?view=graph-rest-1.0) | [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) | Update the properties of an agentIdentityBlueprintPrincipal object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-delete?view=graph-rest-1.0) | None | Delete an agentIdentityBlueprintPrincipal object. |
| **App role assignments** |  |  |
| [List app role assigned to](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignedto?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the users, groups, and agent identities assigned app roles for this agent identity blueprint principal. |
| [Add app role assigned to](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignedto?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Assign an app role for this agent identity blueprint principal to a user, group, or service principal. |
| [Remove app role assigned to](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-approleassignedto?view=graph-rest-1.0) | None | Remove an app role assignment for this agent identity blueprint principal from a user, group, or service principal. |
| [List app role assignments](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the app roles that this agent identity blueprint principal is assigned. |
| [Add app role assignment](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Assign an app role to this agent identity blueprint principal. |
| [Remove app role assignment](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-approleassignments?view=graph-rest-1.0) | None | Remove an app role assignment from this agent identity blueprint principal. |
| **Delegated permission grants** |  |  |
| [List OAuth 2.0 permission grants](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-oauth2permissiongrants?view=graph-rest-1.0) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) collection | Get the delegated permission grants authorizing this agent identity blueprint principal to access an API on behalf of a signed-in user. |
| **Deleted items** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of recently deleted agent identities. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Retrieve the properties of a recently deleted agent identity. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Restore a recently deleted agent identity. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | None | Permanently delete an agent identity. |
| **Directory objects** |  |  |
| [List owned objects](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-list-ownedobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get directory objects owned by this agent identity blueprint principal. |
| [List created objects](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-list-createdobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get directory objects created by this agent identity blueprint principal. |
| **Memberships** |  |  |
| [List member of](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-list-memberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups that this agent identity blueprint principal is a direct member of. |
| **Owners** |  |  |
| [List owners](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-list-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the owners of this agent identity blueprint principal. |
| [Add owners](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-post-owners?view=graph-rest-1.0) | None | Assign an owner to this agent identity blueprint principal. |
| [Remove owners](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-delete-owners?view=graph-rest-1.0) | None | Remove an owner from this agent identity blueprint principal. |
| **Sponsors** |  |  |
| [List sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-list-sponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the sponsors for this agent identity blueprint principal. |
| [Add sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-post-sponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add sponsors by posting to the sponsors collection. |
| [Remove sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-delete-sponsors?view=graph-rest-1.0) | None | Remove a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) object. |

## Properties

Important

While this resource inherits from **servicePrincipal**, some properties are not applicable and return `null` or default values. These properties are excluded from the table below.

| Property | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | `true` if the agent identity blueprint principal account is enabled; otherwise, `false`. If set to `false`, then no users are able to sign in to this app, even if they're assigned to it. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| appDescription | String | The description exposed by the associated agent identity blueprint. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| appDisplayName | String | The display name exposed by the associated agent identity blueprint. Maximum length is 256 characters. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| appId | String | The **appId** of the associated agent identity blueprint. Alternate key. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| appOwnerOrganizationId | Guid | Contains the tenant ID where the agent identity blueprint is registered. This is applicable only to agent identity blueprint principals backed by applications. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| appRoleAssignmentRequired | Boolean | Specifies whether users or other service principals need to be granted an app role assignment for this agent identity blueprint principal before users can sign in or apps can get tokens. The default value is `false`. Not nullable. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| appRoles | [appRole](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) collection | The roles exposed by the agent identity blueprint, which this agent identity blueprint principal represents. For more information, see the **appRoles** property definition on the application entity. Not nullable. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| createdByAppId | String | The **appId** of the application that created this agent identity blueprint principal. Set internally by Microsoft Entra ID. Read-only. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| disabledByMicrosoftStatus | String | Specifies whether Microsoft has disabled the registered agent identity blueprint. The possible values are: `null` \(default value\), `NotDisabled`, and `DisabledDueToViolationOfServicesAgreement` \(reasons may include suspicious, abusive, or malicious activity, or a violation of the Microsoft Services Agreement\). Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| displayName | String | The display name for the agent identity blueprint principal. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| id | String | The unique identifier for the agent identity blueprint principal. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Key. Not nullable. Read-only. |
| info | [informationalUrl](https://learn.microsoft.com/en-us/graph/api/resources/informationalurl?view=graph-rest-1.0) | Basic profile information of the acquired application such as app's marketing, support, terms of service and privacy statement URLs. The terms of service and privacy statement are surfaced to users through the user consent experience. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| managerApplications | Guid collection | The collection of application IDs designated as managers of this agent identity blueprint principal's backing [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0). Read-only; the value is server-managed and reflects the **managerApplications** of the backing agentIdentityBlueprint. To change the managers, an owner or administrator must update the **managerApplications** property on the backing agentIdentityBlueprint **in the tenant where it's registered**. For multitenant agent identity blueprints, admins in a tenant where the blueprint is only consumed can't make this change — they must ask an owner or administrator in the blueprint's home tenant. Not nullable. Returned only on `$select`. |
| publishedPermissionScopes | [permissionScope](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) collection | The delegated permissions exposed by the application. For more information, see the **oauth2PermissionScopes** property on the agent identity blueprint entity's **api** property. Not nullable. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| publisherName | String | The name of the Microsoft Entra tenant that published the application. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| servicePrincipalNames | String collection | Contains the list of **identifiersUris**, copied over from the associated agent identity blueprint. More values can be added to hybrid agent identity blueprint. These values can be used to identify the permissions exposed by this app within Microsoft Entra ID. Not nullable. **Property blocked on Agent Identity Blueprint Principal.** Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| servicePrincipalType | String | Identifies if the agent identity blueprint principal represents an application. This is set by Microsoft Entra ID internally. For an agent identity blueprint principal that represents an application this is set as **Application**. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| signInAudience | String | Specifies the Microsoft accounts that are supported for the current agent identity blueprint. Read-only. Supported values are: `AzureADMyOrg`, `AzureADMultipleOrgs`, `AzureADandPersonalMicrosoftAccount`, and `PersonalMicrosoftAccount`. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| tags | String collection | Custom strings that can be used to categorize and identify the agent identity blueprint principal. Not nullable. The value is the union of strings set here and on the associated agent identity blueprint entity's **tags** property. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| verifiedPublisher | [verifiedPublisher](https://learn.microsoft.com/en-us/graph/api/resources/verifiedpublisher?view=graph-rest-1.0) | Specifies the verified publisher of the application that's linked to this agent identity blueprint principal. Inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appManagementPolicies | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) collection | The appManagementPolicy applied to this agent identity blueprint principal. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| appRoleAssignedTo | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | App role assignments for this agent identity blueprint principal, granted to users, groups, and other service principals. Supports `$expand`. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| appRoleAssignments | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | App role assignment for another app or service, granted to this agent identity blueprint principal. Supports `$expand`. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| createdObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects created by this agent identity blueprint principal. Read-only. Nullable. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| memberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Roles that this agent identity blueprint principal is a member of. HTTP Methods: GET Read-only. Nullable. Supports `$expand`. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| oauth2PermissionGrants | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) collection | Delegated permission grants authorizing this agent identity blueprint principal to access an API on behalf of a signed-in user. Read-only. Nullable. Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| ownedObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects that are owned by this agent identity blueprint principal. Read-only. Nullable. Supports `$expand` and `$filter` \(`/$count eq 0`, `/$count ne 0`, `/$count eq 1`, `/$count ne 1`\). Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| owners | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects that are owners of this agent identity blueprint principal. The owners are a set of nonadmin users or servicePrincipals who are allowed to modify this object. Supports `$expand` and `$filter` \(`/$count eq 0`, `/$count ne 0`, `/$count eq 1`, `/$count ne 1`\). Inherited from [microsoft.graph.servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) |
| sponsors | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The sponsors for this agent identity blueprint principal. Sponsors are users or service principals who can authorize and manage the lifecycle of agent identity instances. |

## JSON representation

The following JSON representation shows the resource type. Only a subset of all properties are returned by default. All other properties can only be retrieved using `$select`.

```json
{
  "@odata.type": "#microsoft.graph.agentIdentityBlueprintPrincipal",
  "id": "String (identifier)",
  "accountEnabled": "Boolean",
  "createdByAppId": "String",
  "appDescription": "String",
  "appDisplayName": "String",
  "appId": "String",
  "appOwnerOrganizationId": "Guid",
  "appRoleAssignmentRequired": "Boolean",
  "disabledByMicrosoftStatus": "String",
  "displayName": "String",
  "publisherName": "String",
  "servicePrincipalNames": [
    "String"
  ],
  "servicePrincipalType": "String",
  "signInAudience": "String",
  "tags": [
    "String"
  ],
  "appRoles": [
    {
      "@odata.type": "microsoft.graph.appRole"
    }
  ],
  "info": {
    "@odata.type": "microsoft.graph.informationalUrl"
  },
  "managerApplications": [
    "Guid"
  ],
  "publishedPermissionScopes": [
    {
      "@odata.type": "microsoft.graph.permissionScope"
    }
  ],
  "verifiedPublisher": {
    "@odata.type": "microsoft.graph.verifiedPublisher"
  }
}
```
