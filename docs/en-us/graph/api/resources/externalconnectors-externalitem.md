<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# externalItem resource type

Namespace: microsoft.graph.externalConnectors

An item added to a Microsoft Graph [connection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-put-items?view=graph-rest-1.0) | [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) | Create a new [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalitem-get?view=graph-rest-1.0) | [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) | Read the properties and relationships of an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalitem-update?view=graph-rest-1.0) | [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) | Update the properties of an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalitem-delete?view=graph-rest-1.0) | None | Delete an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object. |
| [Add activities](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalitem-addactivities?view=graph-rest-1.0) | [microsoft.graph.externalConnectors.externalActivityResult](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0) collection | Append additional instances of [externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0) objects on an **externalItem**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| acl | [microsoft.graph.externalConnectors.acl](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-acl?view=graph-rest-1.0) collection | An array of access control entries. Each entry specifies the access granted to a user or group. Required. |
| content | [microsoft.graph.externalConnectors.externalItemContent](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitemcontent?view=graph-rest-1.0) | A plain-text representation of the contents of the item. The text in this property is full-text indexed. Optional. |
| id | String | Developer-provided unique ID of the item within the containing [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0). Must be alphanumeric and a maximum of 128 characters. Required. |
| properties | [microsoft.graph.externalConnectors.properties](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-properties?view=graph-rest-1.0) | A property bag with the properties of the item. The properties MUST conform to the [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) defined for the [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0). Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activities | [microsoft.graph.externalConnectors.externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0) collection | Returns a list of activities performed on the item. Write-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "acl": [
    {
      "type": "everyone",
      "value": "67a141d8-cf4e-4528-ba07-bed21bfacd2d",
      "accessType": "grant"
    }
  ],
  "content": {
    "@odata.type": "microsoft.graph.externalConnectors.externalItemContent"
  },
  "id": "String (identifier)",
  "properties": {
    "@odata.type": "microsoft.graph.externalConnectors.properties"
  }
}
```
