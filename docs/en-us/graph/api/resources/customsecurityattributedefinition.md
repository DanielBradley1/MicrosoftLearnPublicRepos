<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# customSecurityAttributeDefinition resource type

Namespace: microsoft.graph

Represents the schema of a custom security attribute \(key-value pair\). For example, the custom security attribute name, description, data type, and allowed values.

You can define up to 500 active objects in a tenant. The **customSecurityAttributeDefinition** object can't be renamed or deleted, but it can be deactivated by using the [Update customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-update?view=graph-rest-1.0) operation. Must be part of an [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-customsecurityattributedefinitions?view=graph-rest-1.0) | [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) collection | Get a list of the [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-get?view=graph-rest-1.0) | [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) | Read the properties and relationships of a [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/directory-post-customsecurityattributedefinitions?view=graph-rest-1.0) | [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) | Create a new [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-update?view=graph-rest-1.0) | [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) | Update the properties of a [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attributeSet | String | Name of the attribute set. Case insensitive. |
| description | String | Description of the custom security attribute. Can be up to 128 characters long and include Unicode characters. Can be changed later. |
| id | String | Identifier of the custom security attribute that is a combination of the attribute set name and the custom security attribute name separated by an underscore \(`attributeSet`\_`name`\). The **id** property is auto generated and cannot be set. Case insensitive. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isCollection | Boolean | Indicates whether multiple values can be assigned to the custom security attribute. Cannot be changed later. If **type** is set to `Boolean`, **isCollection** cannot be set to `true`. |
| isSearchable | Boolean | Indicates whether custom security attribute values are indexed for searching on objects that are assigned attribute values. Cannot be changed later. |
| name | String | Name of the custom security attribute. Must be unique within an attribute set. Can be up to 32 characters long and include Unicode characters. Cannot contain spaces or special characters. Cannot be changed later. Case insensitive. |
| status | String | Specifies whether the custom security attribute is active or deactivated. Acceptable values are: `Available` and `Deprecated`. Can be changed later. |
| type | String | Data type for the custom security attribute values. Supported types are: `Boolean`, `Integer`, and `String`. Cannot be changed later. |
| usePreDefinedValuesOnly | Boolean | Indicates whether only predefined values can be assigned to the custom security attribute. If set to `false`, free-form values are allowed. Can later be changed from `true` to `false`, but cannot be changed from `false` to `true`. If **type** is set to `Boolean`, **usePreDefinedValuesOnly** cannot be set to `true`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allowedValues | [allowedValue](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0) collection | Values that are predefined for this custom security attribute. This navigation property is not returned by default and must be specified in an `$expand` query. For example, `/directory/customSecurityAttributeDefinitions?$expand=allowedValues`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customSecurityAttributeDefinition",
  "attributeSet": "String",
  "description": "String",
  "id": "String (identifier)",
  "isCollection": "Boolean",
  "isSearchable": "Boolean",
  "name": "String",
  "status": "String",
  "type": "String",
  "usePreDefinedValuesOnly": "Boolean"
}
```
