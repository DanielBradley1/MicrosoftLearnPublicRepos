<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# configManagerCollection resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A ConfigManager defined collection of devices or users.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List configManagerCollections](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-configmanagercollection-list?view=graph-rest-beta) | [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) collection | List properties and relationships of the [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) objects. |
| [Get configManagerCollection](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-configmanagercollection-get?view=graph-rest-beta) | [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) | Read properties and relationships of the [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) object. |
| [Create configManagerCollection](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-configmanagercollection-create?view=graph-rest-beta) | [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) | Create a new [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) object. |
| [Delete configManagerCollection](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-configmanagercollection-delete?view=graph-rest-beta) | None | Deletes a [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta). |
| [Update configManagerCollection](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-configmanagercollection-update?view=graph-rest-beta) | [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) | Update the properties of a [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) object. |
| [getPolicySummary function](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-configmanagercollection-getpolicysummary?view=graph-rest-beta) | [configManagerPolicySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagerpolicysummary?view=graph-rest-beta) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key for the ConfigManager Collection. |
| displayName | String | The DisplayName. |
| collectionIdentifier | String | The collection identifier in SCCM. |
| hierarchyName | String | The HierarchyName. |
| hierarchyIdentifier | String | The Hierarchy Identifier. |
| createdDateTime | DateTimeOffset | The created date. |
| lastModifiedDateTime | DateTimeOffset | The last modified date. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.configManagerCollection",
  "id": "String (identifier)",
  "displayName": "String",
  "collectionIdentifier": "String",
  "hierarchyName": "String",
  "hierarchyIdentifier": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
