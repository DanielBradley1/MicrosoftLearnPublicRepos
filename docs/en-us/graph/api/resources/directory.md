<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# directory resource type

Namespace: microsoft.graph

Represents a deleted item in the directory. When an item is deleted, it moves to the deleted items container. Deleted items remain available to restore for up to 30 days. After 30 days, the items are permanently deleted.

Currently, deleted items functionality is supported for the the following resources:

- [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0)
- [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0)
- [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0)
- [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Gets a list of recently deleted items. |
| [List remote tenant groups](https://learn.microsoft.com/en-us/graph/api/directory-list-remotetenantgroups?view=graph-rest-1.0) | [remoteTenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/remotetenantgroup?view=graph-rest-1.0) collection | Gets a list of the remote tenant groups in the directory. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Gets the properties of a deleted item. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Restores a recently deleted item. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | None | Permanently deletes an item. |
| [List deleted items owned by user](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-getuserownedobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Lists directory items owned by a user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique identifier for the object; for example, `12345678-9abc-def0-1234-56789abcde`. Key. Not nullable. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| administrativeUnits | [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) collection | Conceptual container for user and group directory objects. |
| attributeSets | [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) collection | Group of related custom security attribute definitions. |
| customSecurityAttributeDefinitions | [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) collection | Schema of a custom security attributes \(key-value pairs\). |
| deletedItems | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Recently deleted items. Read-only. Nullable. |
| deviceLocalCredentials | [deviceLocalCredential](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredential?view=graph-rest-1.0) collection | The credentials of the device's local administrator account backed up to Microsoft Entra ID. |
| federationConfigurations | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0) collection | Configure domain federation with organizations whose identity provider \(IdP\) supports either the SAML or WS-Fed protocol. |
| onPremisesSynchronization | [onPremisesDirectorySynchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) | A container for on-premises directory synchronization functionalities that are available for the organization. |
| publicKeyInfrastructure | [publicKeyInfrastructureRoot](https://learn.microsoft.com/en-us/graph/api/resources/publickeyinfrastructureroot?view=graph-rest-1.0) | The collection of public key infrastructure instances for the certificate-based authentication feature for users in a Microsoft Entra tenant. |
| remoteTenantGroups | [remoteTenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/remotetenantgroup?view=graph-rest-1.0) collection | Collection of groups in remote Microsoft Entra tenants that are available in the directory. |
| subscriptions | [companySubscription](https://learn.microsoft.com/en-us/graph/api/resources/companysubscription?view=graph-rest-1.0) collection | List of commercial subscriptions that an organization acquired. |
| tenantGovernance | [microsoft.graph.tenantGovernance](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernance?view=graph-rest-1.0) | Container for Microsoft Entra Tenant Governance capabilities. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.directory"
}
```
