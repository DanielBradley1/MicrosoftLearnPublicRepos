<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# siteSource resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

The container for a site associated with a [custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List siteSources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-list-sitesources?view=graph-rest-beta) | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) collection | Get a list of **siteSource** objects and their properties. |
| [Create siteSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-post-sitesources?view=graph-rest-beta) | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) | Create a new **siteSource** object. |
| [Get siteSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-sitesource-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) | Read the properties and relationships of a **siteSource** object. |
| [Delete siteSource](https://learn.microsoft.com/en-us/graph/api/ediscovery-sitesource-delete?view=graph-rest-beta) | None | Delete a **siteSource** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the **siteSource**. |
| createdDateTime | DateTimeOffset | The date and time the **siteSource** was created. |
| displayName | String | The display name of the **siteSource**. This will be the name of the SharePoint site. |
| id | String | The ID of the **siteSource**. The site source can be retrieved at any time with [Get site](https://learn.microsoft.com/en-us/graph/api/site-get?view=graph-rest-beta) - `https://graph.microsoft.com/v1.0/sites/{siteId}` |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| site | [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta) | The SharePoint site associated with the **siteSource**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.siteSource",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "id": "String (identifier)"
}
```
