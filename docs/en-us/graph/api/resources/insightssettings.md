<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# insightsSettings resource type

Namespace: microsoft.graph

Represents settings to calculate and manage the display or programmatic return of a specific type of insights in an organization.

Item insights and [meeting hours insights](https://support.microsoft.com/office/suggested-meeting-hours-0613d113-d7c1-4faa-bb11-c8ba30a78ef1) represent relationships between users and items such as documents, sites, and other content types in Microsoft 365. Programmatically, they're represented by the [itemInsights](https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0) resource. You can get documents that are [shared \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/insights-list-shared?view=graph-rest-1.0) with a user, [trending](https://learn.microsoft.com/en-us/graph/api/insights-list-trending?view=graph-rest-1.0) around a user, or [used \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/insights-list-used?view=graph-rest-1.0) by a user. You can use **insightsSettings** to [customize the privacy settings for calculating, displaying, or returning item insights in an organization](https://learn.microsoft.com/en-us/graph/insights-customize-item-insights-privacy).

In contrast, for item insights and [meeting hours insights](https://support.microsoft.com/office/update-your-meeting-hours-using-the-profile-card-0613d113-d7c1-4faa-bb11-c8ba30a78ef1), you can also manage their calculation and visibility at a user level by using the [userInsightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/userinsightssettings?view=graph-rest-1.0) resource.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List itemInsights](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-iteminsights?view=graph-rest-1.0) | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) | Get the properties of an [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) object to display or return item insights in an organization. |
| [Update insightsSettings](https://learn.microsoft.com/en-us/graph/api/insightssettings-update?view=graph-rest-1.0) | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) | Update privacy settings to display or return the specified type of insights in an organization. Currently, [itemInsights](https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0) is the only supported type of settings. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledForGroup | String | The ID of a Microsoft Entra group, of which the specified type of insights are disabled for its members. The default value is `null`. Optional. |
| isEnabledInOrganization | Boolean | `true` if insights of the specified type are enabled for the organization; `false` if insights of the specified type are disabled for all users without exceptions. The default value is `true`. Optional. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "disabledForGroup": "String",
  "isEnabledInOrganization": "Boolean"
}
```
