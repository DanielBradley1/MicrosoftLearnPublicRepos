<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# userSource resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

The container for a [custodian's](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) mailbox and OneDrive for Business site.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List userSources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-list-usersources?view=graph-rest-beta) | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) collection | Get a list of the **userSource** objects and their properties. |
| [Create userSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-post-usersources?view=graph-rest-beta) | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) | Create a new **userSource** object. |
| [Get userSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-usersource-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) | Read the properties and relationships of a **userSource** object. |
| [Delete userSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-usersource-delete?view=graph-rest-beta) | None | Delete a **userSource** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the **userSource**. |
| createdDateTime | DateTimeOffset | The date and time the **userSource** was created |
| displayName | String | The display name associated with the mailbox and site. |
| email | String | Email address of the user's mailbox. |
| id | String | The ID of the **userSource**. This is not the ID of the actual group |
| includedSources | microsoft.graph.ediscovery.sourceType | Specifies which sources are included in this group. The possible values are: `mailbox`, `site`. |
| siteWebUrl | String | The URL of the user's OneDrive for Business site. Read-only. |

### sourceType values

Types of source related to the user. Includes mailbox and site by default.

| Member | Description |
| :--- | --- |
| mailbox | Represents a mailbox. |
| site | Represents a OneDrive for Business site. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.userSource",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "id": "String (identifier)",
  "email": "String",
  "includedSources": "String"
}
```
