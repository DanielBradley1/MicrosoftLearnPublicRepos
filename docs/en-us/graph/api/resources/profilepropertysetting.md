<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# profilePropertySetting resource type

Namespace: microsoft.graph

Represents a collection of configuration data for property-level settings configured by an administrator.

Note

When you configure the **prioritizedSourceUrls** setting, the **name** property *must* be empty to differentiate it from other property-level settings in the collection that have a **name** property. Only one configuration without a name is allowed per collection.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-profilepropertysettings?view=graph-rest-1.0) | [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) collection | Get a collection of [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) objects that define the configuration for user profile properties in an organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilepropertysettings?view=graph-rest-1.0) | [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) | Create a new [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/profilepropertysetting-get?view=graph-rest-1.0) | [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) | Read the properties and relationships of a [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/profilepropertysetting-update?view=graph-rest-1.0) | [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) | Update the properties of a [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/profilepropertysetting-delete?view=graph-rest-1.0) | None | Delete a [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the property-level setting. |
| id | String | System generated GUID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| name | String | Other name of the property-level setting. For backward compatibility. |
| prioritizedSourceUrls | String collection | A collection of prioritized profile source URLs ordered by data precedence within an organization. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.profilePropertySetting",
  "id": "String (identifier)",
  "name": "String",
  "displayName": "String",
  "prioritizedSourceUrls": [
    "String"
  ]
}
```
