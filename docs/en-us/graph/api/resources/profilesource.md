<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# profileSource resource type

Namespace: microsoft.graph

Represents the configuration data of a profile source created by an organization administrator. This configuration represents the source of profile data in a way that is understandable to end users.

For more information, see [Manage profile source settings for an organization using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/profilesource-configure-settings).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-profilesources?view=graph-rest-1.0) | [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) collection | Get a list of the [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) objects and their properties, which represent both external data sources and out-of-the-box Microsoft data sources configured for user profiles in an organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilesources?view=graph-rest-1.0) | [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) | Create a new [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/profilesource-get?view=graph-rest-1.0) | [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) | Read the properties and relationships of a [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/profilesource-update?view=graph-rest-1.0) | [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) | Update the properties of a [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/profilesource-delete?view=graph-rest-1.0) | None | Delete a [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the profile source intended to inform users about the profile source name. |
| id | String | System-generated GUID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| kind | String | Type of the profile source. |
| localizations | [profileSourceLocalization](https://learn.microsoft.com/en-us/graph/api/resources/profilesourcelocalization?view=graph-rest-1.0) collection | Alternative localized labels specified by an administrator. |
| sourceId | String | Profile source identifier used as an [alternate key](https://github.com/microsoft/api-guidelines/blob/vNext/graph/patterns/alternate-key.md). |
| webUrl | String | Web URL of the profile source that directs users to the page view of the profile data. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.profileSource",
  "displayName": "String",
  "id": "String (identifier)",
  "kind": "String",
  "localizations": [{"@odata.type": "microsoft.graph.profileSourceLocalization"}],
  "sourceId": "String",
  "webUrl": "String"
}
```
