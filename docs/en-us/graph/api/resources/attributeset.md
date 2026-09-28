<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# attributeSet resource type

Namespace: microsoft.graph

Represents a group of related custom security attribute definitions.

You can define up to 500 **attributeSet** objects in a tenant. The **attributeSet** object can't be renamed or deleted.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-attributesets?view=graph-rest-1.0) | [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) collection | Get a list of the [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/attributeset-get?view=graph-rest-1.0) | [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) | Read the properties and relationships of an [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/directory-post-attributesets?view=graph-rest-1.0) | [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) | Create a new [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/attributeset-update?view=graph-rest-1.0) | [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) | Update the properties of an [attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the attribute set. Can be up to 128 characters long and include Unicode characters. Can be changed later. |
| id | String | Identifier for the attribute set that is unique within a tenant. Can be up to 32 characters long and include Unicode characters. Cannot contain spaces or special characters. Cannot be changed later. Case insensitive. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| maxAttributesPerSet | Int32 | Maximum number of custom security attributes that can be defined in this attribute set. Default value is `null`. If not specified, the administrator can add up to the maximum of 500 active attributes per tenant. Can be changed later. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attributeSet",
  "description": "String",
  "id": "String (identifier)",
  "maxAttributesPerSet": "Int32"
}
```
