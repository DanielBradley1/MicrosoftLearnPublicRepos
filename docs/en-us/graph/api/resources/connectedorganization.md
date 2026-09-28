<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# connectedOrganization resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), a connected organization is a reference to a directory or domain of another organization whose users can request access.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-connectedorganizations?view=graph-rest-1.0) | [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) collection | Retrieve a list of connectedOrganization objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-connectedorganizations?view=graph-rest-1.0) | [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) | Create a new connectedOrganization object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/connectedorganization-get?view=graph-rest-1.0) | [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) | Read properties and relationships of a connectedOrganization object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/connectedorganization-update?view=graph-rest-1.0) | [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) collection | Update a connectedOrganization. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/connectedorganization-delete?view=graph-rest-1.0) | None | Delete a connectedOrganization. |
| **External sponsors** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/connectedorganization-list-externalsponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of a connectedOrganization's external sponsors. |
| [Add](https://learn.microsoft.com/en-us/graph/api/connectedorganization-post-externalsponsors?view=graph-rest-1.0) | None | Add a user or group to a connectedOrganization's external sponsors. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/connectedorganization-delete-externalsponsors?view=graph-rest-1.0) | None | Remove a user or group from the connectedOrganization's external sponsors. |
| **Internal sponsors** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/connectedorganization-list-internalsponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of a connectedOrganization's internal sponsors. |
| [Add](https://learn.microsoft.com/en-us/graph/api/connectedorganization-post-internalsponsors?view=graph-rest-1.0) | None | Add a user or group to a connectedOrganization's internal sponsors. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/connectedorganization-delete-internalsponsors?view=graph-rest-1.0) | None | Remove a user or group from the connectedOrganization's internal sponsors. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| description | String | The description of the connected organization. |
| displayName | String | The display name of the connected organization. Supports `$filter` \(`eq`\). |
| id | String | Read-only. |
| identitySources | [identitySource](https://learn.microsoft.com/en-us/graph/api/resources/identitysource?view=graph-rest-1.0) collection | The identity sources in this connected organization, one of [azureActiveDirectoryTenant](https://learn.microsoft.com/en-us/graph/api/resources/azureactivedirectorytenant?view=graph-rest-1.0), [crossCloudAzureActiveDirectoryTenant](https://learn.microsoft.com/en-us/graph/api/resources/crosscloudazureactivedirectorytenant?view=graph-rest-1.0), [domainIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/domainidentitysource?view=graph-rest-1.0), [externalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/externaldomainfederation?view=graph-rest-1.0), or [socialIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/socialidentitysource?view=graph-rest-1.0). Nullable. |
| modifiedDateTime | DateTimeOffset | \*The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| state | connectedOrganizationState | The state of a connected organization defines whether assignment policies with requestor scope type `AllConfiguredConnectedOrganizationSubjects` are applicable or not. The possible values are: `configured`, `proposed`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| externalSponsors | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Nullable. |
| internalSponsors | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.connectedOrganization",
  "description": "String",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "identitySources": [
    {
      "@odata.type": "microsoft.graph.azureActiveDirectoryTenant"
    }
  ],
  "modifiedDateTime": "String (timestamp)",
  "state": "String"
}
```
