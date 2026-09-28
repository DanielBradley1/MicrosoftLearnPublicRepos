<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# allowedValue resource type

Namespace: microsoft.graph

Represents a predefined value that is allowed for a custom security attribute definition.

You can define up to 100 **allowedValue** objects per [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0). The **allowedValue** object can't be renamed or deleted, but it can be deactivated by using the [Update allowedValue](https://learn.microsoft.com/en-us/graph/api/allowedvalue-update?view=graph-rest-1.0) operation. This object is defined as a navigation property on the [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) resource and its value is returned only on `$expand`.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-list-allowedvalues?view=graph-rest-1.0) | [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) collection | Get a list of the [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/allowedvalue-get?view=graph-rest-1.0) | [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) | Read the properties and relationships of an [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-post-allowedvalues?view=graph-rest-1.0) | [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) | Create a new [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/allowedvalue-update?view=graph-rest-1.0) | [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) | Update the properties of an [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier for the predefined value. Can be up to 64 characters long and include Unicode characters. Can include spaces, but some special characters aren't allowed. Can't be changed later. Case sensitive. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isActive | Boolean | Indicates whether the predefined value is active or deactivated. If set to `false`, this predefined value can't be assigned to any other supported directory objects. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.allowedValue",
  "id": "String (identifier)",
  "isActive": "Boolean"
}
```
