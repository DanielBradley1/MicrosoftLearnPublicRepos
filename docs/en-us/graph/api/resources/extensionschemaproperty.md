<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/extensionschemaproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# extensionSchemaProperty resource type

Namespace: microsoft.graph

Use the **extensionSchemaProperty** resource to define a property's name and its type, as part of a [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension?view=graph-rest-1.0) definition.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the strongly typed property defined as part of a schema extension. |
| type | String | The type of the property that is defined as part of a schema extension. Allowed values are `Binary`, `Boolean`, `DateTime`, `Integer`, or `String`. For more information, see [Supported property data types](#supported-property-data-types). |

### Supported property data types

The following data types are supported when defining a property in a schema extension:

| Property Type | Remarks |
| --- | --- |
| Binary | 256 bytes maximum. |
| Boolean | Not supported for contacts, messages, events, and posts. |
| DateTime | Must be specified in ISO 8601 format and is stored in UTC. |
| Integer | 32-bit value. Not supported for contacts, messages, events and posts. |
| String | 256 characters maximum. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "String",
  "type": "String"
}
```
