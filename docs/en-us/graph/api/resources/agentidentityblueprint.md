<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# agentIdentityBlueprint resource type

Namespace: microsoft.graph

An agent identity blueprint serves as a template for creating agent identities within the Microsoft Entra ID ecosystem.

Inherits from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0).

This resource is an open type that allows additional properties beyond those documented here.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-list?view=graph-rest-1.0) | [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) collection | Get a list of the agentIdentityBlueprint objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-post?view=graph-rest-1.0) | [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) | Create \(register\) a new agentIdentityBlueprint. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-get?view=graph-rest-1.0) | [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) | Read the properties and relationships of [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-update?view=graph-rest-1.0) | [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) | Update the properties of an agentIdentityBlueprint object. |
| [Upsert](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-upsert?view=graph-rest-1.0) | [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) | Create a new agent identity blueprint if it doesn't exist, or update the properties of an existing blueprint. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-delete?view=graph-rest-1.0) | None | Delete an agentIdentityBlueprint object. |
| **Credentials** |  |  |
| [Add password](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-addpassword?view=graph-rest-1.0) | [passwordCredential](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) | Add a strong password or secret to an agent identity blueprint. |
| [Remove password](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-removepassword?view=graph-rest-1.0) | [passwordCredential](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) | Remove a password or secret from an agent identity blueprint. |
| [Add key](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-addkey?view=graph-rest-1.0) | [keyCredential](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0) | Add a key credential to an agent identity blueprint. |
| [Remove key](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-removekey?view=graph-rest-1.0) | None | Remove a key credential from an agent identity blueprint. |
| [List federated identity credential](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-list?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) collection | Get a list of the [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) objects and their properties. |
| [Create federated identity credential](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-post?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) | Create a new [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Get federated identity credential](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-get?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) | Read the properties and relationships of a [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Update federated identity credential](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-update?view=graph-rest-1.0) | None | Update the properties of a [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Upsert federated identity credential](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-upsert?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) | Create a new [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) if it doesn't exist, or update the properties of an existing [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Delete federated identity credential](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-delete?view=graph-rest-1.0) | None | Delete a [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| **Deleted items** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of recently deleted agent identities. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Retrieve the properties of a recently deleted agent identity. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Restore a recently deleted agent identity. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | None | Permanently delete an agent identity. |
| **Owners** |  |  |
| [List owners](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-list-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the owners of this agent identity blueprint principal. |
| [Add owners](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-post-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Assign an owner to this agent identity blueprint principal. |
| [Remove owners](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-delete-owners?view=graph-rest-1.0) | None | Remove an owner from this agent identity blueprint principal. |
| **Sponsors** |  |  |
| [List sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-list-sponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the sponsors for this agent identity blueprint. Sponsors are users or service principals who can authorize and manage the lifecycle of agent identity instances. |
| [Add sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-post-sponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add sponsors by posting to the sponsors collection. |
| [Remove sponsors](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-delete-sponsors?view=graph-rest-1.0) | None | Remove a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) object. |
| **Verified publisher** |  |  |
| [Set](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-setverifiedpublisher?view=graph-rest-1.0) | None | Set the verified publisher of an application. |
| [Unset](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-unsetverifiedpublisher?view=graph-rest-1.0) | None | Unset the verified publisher of an application. |

## Properties

Important

While this resource inherits from **application**, some properties are not applicable and return `null` or default values. These properties are excluded from the table below.

| Property | Type | Description |
| :--- | :--- | :--- |
| api | [apiApplication](https://learn.microsoft.com/en-us/graph/api/resources/apiapplication?view=graph-rest-1.0) | Specifies settings for an agent identity blueprint that implements a web API. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| appId | String | The unique identifier for the agent identity blueprint that is assigned by Microsoft Entra ID. Not nullable. Read-only. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| appRoles | [appRole](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) collection | The collection of roles defined for the agent identity blueprint. With app role assignments, these roles can be assigned to users, groups, or service principals associated with other applications. Not nullable. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| certification | [certification](https://learn.microsoft.com/en-us/graph/api/resources/certification?view=graph-rest-1.0) | Specifies the certification status of the agent identity blueprint. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| createdByAppId | String | The **appId** of the application that created this agent identity blueprint. Set internally by Microsoft Entra ID. Read-only. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the agent identity blueprint was registered. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. Read-only. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| description | String | Free text field to provide a description of the agent identity blueprint to end users. The maximum allowed size is 1,024 characters. The least privileged permission to update this property is *AgentIdentityBlueprint.UpdateBranding.All*. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| disabledByMicrosoftStatus | String | Specifies whether Microsoft has disabled the registered agent identity blueprint. The possible values are: `null` \(default value\), `NotDisabled`, and `DisabledDueToViolationOfServicesAgreement` \(reasons may include suspicious, abusive, or malicious activity, or a violation of the Microsoft Services Agreement\). Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| displayName | String | The display name for the agent identity blueprint. Maximum length is 256 characters. The least privileged permission to update this property is *AgentIdentityBlueprint.UpdateBranding.All*. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| groupMembershipClaims | String | Configures the `groups` claim issued in a user or OAuth 2.0 access token that the agent identity blueprint expects. To set this attribute, use one of the following string values: `None`, `SecurityGroup` \(for security groups and Microsoft Entra roles\), `All` \(this gets all security groups, distribution groups, and Microsoft Entra directory roles that the signed-in user is a member of\). Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| id | String | Unique identifier for the agent identity blueprint object. This property is referred to as **Object ID** in the Microsoft Entra admin center. Key. Not nullable. Read-only. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| identifierUris | String collection | Also known as App ID URI, this value is set when an agent identity blueprint is used as a resource app. The identifierUris acts as the prefix for the scopes you reference in your API's code, and it must be globally unique across Microsoft Entra ID. Not nullable. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| info | [informationalUrl](https://learn.microsoft.com/en-us/graph/api/resources/informationalurl?view=graph-rest-1.0) | Basic profile information of the agent identity blueprint, such as it's marketing, support, terms of service, and privacy statement URLs. The terms of service and privacy statement are surfaced to users through the user consent experience. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| keyCredentials | [keyCredential](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0) collection | The collection of key credentials associated with the agent identity blueprint. Not nullable. The least privileged permission to update this property is *AgentIdentityBlueprint.AddRemoveCreds.All*. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| managerApplications | Guid collection | A collection of application IDs for Microsoft first-party applications designated as managers of this agent blueprint. Manager applications can create agent blueprint principals, agent identities, and agent users for managed agent blueprints without requiring highly privileged permissions such as `AgentIdentityBlueprintPrincipal.ReadWrite.All`. Limited to a maximum of 10 entries. Not nullable. Only Microsoft first-party applications can be designated as managers. Not returned by default. Supports `$select`. |
| optionalClaims | [optionalClaims](https://learn.microsoft.com/en-us/graph/api/resources/optionalclaims?view=graph-rest-1.0) | Application developers can configure optional claims in their Microsoft Entra agent identity blueprints to specify the claims that are sent to their application by the Microsoft security token service. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| passwordCredentials | [passwordCredential](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) collection | The collection of password credentials associated with the agent identity blueprint. Not nullable. The least privileged permission to update this property is *AgentIdentityBlueprint.AddRemoveCreds.All*. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0).  <br>  <br>You can also add passwords after creating the agent identity blueprint by calling the [Add password](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-addpassword?view=graph-rest-1.0) API. |
| publisherDomain | String | The verified publisher domain for the agent identity blueprint. Read-only. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| requiredResourceAccess | [requiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/requiredresourceaccess?view=graph-rest-1.0) collection | Specifies the resources that the agentIdentityBlueprint needs to access. This property also specifies the set of delegated permissions and application roles that it needs for each of those resources. This configuration of access to the required resources drives the consent experience.  <br>  <br>No more than 50 resource services \(APIs\) can be configured. The total number of required permissions must not exceed 400. For more information, see [Limits on requested permissions per app](#limits-on-requested-permissions-per-app). Not nullable. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0).  <br>  <br>Supports `$filter` \(`eq`, `not`, `ge`, `le`\). |
| serviceManagementReference | String | References application or service contact information from a Service or Asset Management database. Nullable. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| signInAudience | String | Specifies the Microsoft accounts that are supported for the current agent identity blueprint. The possible values are: `AzureADMyOrg` \(default\), `AzureADMultipleOrgs`, `AzureADandPersonalMicrosoftAccount`, and `PersonalMicrosoftAccount`. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| tags | String collection | Custom strings that can be used to categorize and identify the agent identity blueprint. Not nullable. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| tokenEncryptionKeyId | Guid | Specifies the keyId of a public key from the keyCredentials collection. When configured, Microsoft Entra ID encrypts all the tokens it emits by using the key this property points to. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| uniqueName | String | The unique identifier that can be assigned to an agent identity blueprint and used as an alternate key. Immutable. Read-only. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| verifiedPublisher | [verifiedPublisher](https://learn.microsoft.com/en-us/graph/api/resources/verifiedpublisher?view=graph-rest-1.0) | Specifies the verified publisher of the agent identity blueprint. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |
| web | [webApplication](https://learn.microsoft.com/en-us/graph/api/resources/webapplication?view=graph-rest-1.0) | Specifies settings for a web application. Inherited from [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). |

### Limits on requested permissions per app

Microsoft Entra ID limits the number of permissions that can be requested and consented by a client app. These limits depend on the `signInAudience` value for an app, shown in the [app's manifest](https://learn.microsoft.com/en-us/graph/api/resources/application).

| signInAudience | Allowed users | Maximum permissions the app can request | Maximum Microsoft Graph permissions the app can request | Maximum permissions that can be consented in a single request |
| --- | --- | --- | --- | --- |
| AzureADMyOrg | Users from the organization where the app is registered | 400 | 400 | About 155 delegated permissions and about 300 application permissions |
| AzureADMultipleOrgs | Users from any Microsoft Entra organization | 400 | 400 | About 155 delegated permissions and about 300 application permissions |
| PersonalMicrosoftAccount | Consumer users \(such as Outlook.com or Live.com accounts\) | 30 | 30 | 30 |
| AzureADandPersonalMicrosoftAccount | Consumer users and users from any Microsoft Entra organization | 30 | 30 | 30 |

Note

For Microsoft Entra Agent ID, some high-risk Microsoft Graph permissions are globally blocked for agents and can't be granted to agent identities.

If you include a blocked Microsoft Graph delegated permission scope or app role in the `resourceAccess` collection of a `requiredResourceAccess` entry, the request is rejected with an HTTP `400 Bad Request` response and an error indicating that the permission is blocked and can't be granted to agent identities.

For the list of blocked Microsoft Graph permissions for agents, see [Microsoft Graph permissions blocked for agents](https://learn.microsoft.com/en-us/graph/api/resources/agentid-platform-overview?view=graph-rest-beta#microsoft-graph-permissions-blocked-for-agents).

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appManagementPolicies | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) collection | The appManagementPolicy applied to this agent identity blueprint. Inherited from [microsoft.graph.application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) |
| federatedIdentityCredentials | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) collection | Federated identities for agent identity blueprints. Inherited from [microsoft.graph.application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) |
| inheritablePermissions | [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) collection | Defines scopes of a resource application that may be automatically granted to agent identities without additional consent. |
| owners | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects that are owners of this agent identity blueprint. The owners are a set of nonadmin users or service principals allowed to modify this object. Read-only. Nullable. Inherited from [microsoft.graph.application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) |
| sponsors | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The sponsors for this agent identity blueprint. Sponsors are users or groups who can authorize and manage the lifecycle of agent identity instances. Required during the create operation. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentIdentityBlueprint",
  "id": "String (identifier)",
  "appId": "String",
  "identifierUris": ["String"],
  "createdByAppId": "String",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "disabledByMicrosoftStatus": "String",
  "displayName": "String",
  "groupMembershipClaims": "String",
  "publisherDomain": "String",
  "requiredResourceAccess": [{"@odata.type": "microsoft.graph.requiredResourceAccess"}],
  "signInAudience": "String",
  "tags": ["String"],
  "tokenEncryptionKeyId": "Guid",
  "uniqueName": "String",
  "serviceManagementReference": "String",
  "certification": {
    "@odata.type": "microsoft.graph.certification"
  },
  "optionalClaims": {
    "@odata.type": "microsoft.graph.optionalClaims"
  },
  "api": {
    "@odata.type": "microsoft.graph.apiApplication"
  },
  "appRoles": [
    {
      "@odata.type": "microsoft.graph.appRole"
    }
  ],
  "info": {
    "@odata.type": "microsoft.graph.informationalUrl"
  },
  "keyCredentials": [
    {
      "@odata.type": "microsoft.graph.keyCredential"
    }
  ],
  "managerApplications": ["Guid"],
  "passwordCredentials": [
    {
      "@odata.type": "microsoft.graph.passwordCredential"
    }
  ],
  "verifiedPublisher": {
    "@odata.type": "microsoft.graph.verifiedPublisher"
  },
  "web": {
    "@odata.type": "microsoft.graph.webApplication"
  }
}
```
