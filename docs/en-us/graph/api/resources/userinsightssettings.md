<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userinsightssettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# userInsightsSettings resource type

Namespace: microsoft.graph

Represents user privacy settings for [itemInsights](https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0) and [meeting hours insights](https://support.microsoft.com/office/update-your-meeting-hours-using-the-profile-card-0613d113-d7c1-4faa-bb11-c8ba30a78ef1). Use this resource to enable or disable the calculation and visibility of item insights and meeting hours insights for a user.

- Item insights: Calculates the relationships between users and items such as documents or sites in Microsoft 365.
- Meeting hours insights: Calculates a person's calendar meeting hours based on activities in Word, Excel, PowerPoint, email, and Outlook calendar in Microsoft 365.

Use the [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) resource to enable or disable the calculation and visibility of item insights, meeting hours insights, and people insights at the organizational level.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/userinsightssettings-get?view=graph-rest-1.0) | [userInsightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/userinsightssettings?view=graph-rest-1.0) | Get the user-customizable privacy settings for [itemInsights](https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0) and [meeting hours insights](https://support.microsoft.com/office/update-your-meeting-hours-using-the-profile-card-0613d113-d7c1-4faa-bb11-c8ba30a78ef1). |
| [Update](https://learn.microsoft.com/en-us/graph/api/userinsightssettings-update?view=graph-rest-1.0) | [userInsightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/userinsightssettings?view=graph-rest-1.0) | Update the privacy settings for [itemInsights](https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0) and [meeting hours insights](https://support.microsoft.com/office/update-your-meeting-hours-using-the-profile-card-0613d113-d7c1-4faa-bb11-c8ba30a78ef1) of a user. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| isEnabled | Boolean | `True` if the user's **itemInsights** and meeting hours insights are enabled; `false` if the user's **itemInsights** and meeting hours insights are disabled. The default value is `true`. Optional. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isEnabled": "Boolean"
}
```
