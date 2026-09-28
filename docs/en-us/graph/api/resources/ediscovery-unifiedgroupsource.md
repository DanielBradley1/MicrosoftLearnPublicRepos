<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-unifiedgroupsource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# unifiedGroupSource resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

The container for a [custodian's](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) group.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List unifiedGroupSources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-list-unifiedgroupsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-unifiedgroupsource?view=graph-rest-beta) collection | Get a list of the **unifiedGroupSource** objects and their properties. |
| [Create unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-post-unifiedgroupsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-unifiedgroupsource?view=graph-rest-beta) | Create a new **unifiedGroupSource** object. |
| [Get unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-unifiedgroupsource-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-unifiedgroupsource?view=graph-rest-beta) | Read the properties and relationships of a **unifiedGroupSource** object. |
| [Delete unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-unifiedgroupsource-delete?view=graph-rest-beta) | None | Delete a **unifiedGroupSource** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the **unifiedGroupSource**. |
| createdDateTime | DateTimeOffset | The date and time the **unifiedGroupSource** was created. |
| displayName | String | The display name of the unified group - This is the name of the group. |
| id | String | The ID of the **unifiedGroupSource**. This isn't the ID of the actual group. |
| includedSources | microsoft.graph.ediscovery.sourceType | Specifies which sources are included in this group. The possible values are: `mailbox`, `site`. |

### sourceType values

Types of source related to the user. Includes mailbox and site both by default.

| Member | Description |
| :--- | --- |
| mailbox | Represents a mailbox. |
| site | Represents a SharePoint site. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) | The group associated with the **unifiedGroupSource**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.ediscovery.unifiedGroupSource",
    "displayName": "Developers group",
    "createdDateTime": "2020-10-27T15:14:11.0048392Z",
    "id": "33434233-3030-3739-3043-393039324633",
    "includedSources": "mailbox,site",
    "createdBy": { "@odata.type": "microsoft.graph.identitySet" }
}
```
