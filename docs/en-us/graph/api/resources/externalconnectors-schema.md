<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# schema resource type

Namespace: microsoft.graph.externalConnectors

The [connection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) schema determines how your external content will be used in various Microsoft Graph experiences. Schema is a flat list of all the properties that you plan to add to the connection along with their attributes, labels, and aliases. You must register the schema before adding items into the connection.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-patch-schema?view=graph-rest-1.0) | [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) | Create a new [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalconnectors-schema-get?view=graph-rest-1.0) | [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) | Read the properties and relationships of a [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| baseType | String | Must be set to `microsoft.graph.externalConnector.externalItem`. Required. |
| properties | [property](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-property?view=graph-rest-1.0) collection | The properties defined for the items in the connection. The minimum number of properties is one, the maximum is 128. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "baseType": "String",
  "properties": [
    {
      "name": "String",
      "type": "String"
    }
  ]
}
```
