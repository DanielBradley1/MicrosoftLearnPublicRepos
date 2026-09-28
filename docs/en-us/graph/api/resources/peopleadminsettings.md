<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/peopleadminsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# peopleAdminSettings resource type

Namespace: microsoft.graph

Represents a setting to control people-related admin settings in the tenant.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-get?view=graph-rest-1.0) | [peopleAdminSettings](https://learn.microsoft.com/en-us/graph/api/resources/peopleadminsettings?view=graph-rest-1.0) | Retrieve the properties and relationships of a [peopleAdminSettings](https://learn.microsoft.com/en-us/graph/api/resources/peopleadminsettings?view=graph-rest-1.0) object. |
| [List item insights](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-iteminsights?view=graph-rest-1.0) | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) | Get the properties of an [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) object to display or return item insights in an organization. |
| [List pronouns settings](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-pronouns?view=graph-rest-1.0) | [pronounsSettings](https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0) collection | Get the properties of the [pronounsSettings](https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0) resource for an organization. |
| [List profile card properties](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-profilecardproperties?view=graph-rest-1.0) | [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) collection | Get a collection of [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) resources for an organization. |
| [Create profile card property](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilecardproperties?view=graph-rest-1.0) | [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) | Create a new [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) for an organization. |
| [List profile sources](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-profilesources?view=graph-rest-1.0) | [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) collection | Get a list of the [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) objects and their properties, which represent both external data sources and out-of-the-box Microsoft data sources configured for user profiles in an organization. |
| [Create profile source](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilesources?view=graph-rest-1.0) | [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) | Create a new [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) object. |
| [List profile property settings](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-profilepropertysettings?view=graph-rest-1.0) | [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) collection | Get a collection of [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) objects that define the configuration for user profile properties in an organization. |
| [Create profile property setting](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilepropertysettings?view=graph-rest-1.0) | [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) | Create a new [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for a **peopleAdminSettings** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| itemInsights | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) | Represents administrator settings that manage the support for item insights in an organization. |
| profileCardProperties | [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) collection | Contains a collection of the properties an administrator has defined as visible on the Microsoft 365 profile card. |
| profilePropertySettings | [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) collection | A collection of profile property configuration settings defined by an administrator for an organization. |
| profileSources | [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) collection | A collection of profile source settings configured by an administrator in an organization. |
| pronouns | [pronounsSettings](https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0) | Represents administrator settings that manage the support of pronouns in an organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.peopleAdminSettings",
  "id": "String (identifier)"
}
```
