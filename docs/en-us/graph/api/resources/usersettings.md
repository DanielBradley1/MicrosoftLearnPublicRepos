<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usersettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# userSettings resource type

Namespace: microsoft.graph

Represents the current user settings for content discovery. The user's preferences apply to the following resources:

- [Exchange settings](https://learn.microsoft.com/en-us/graph/api/resources/exchangesettings?view=graph-rest-1.0)
- [Item insights](https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights?view=graph-rest-1.0)
- [Work hours and locations](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0)

Access the user's [Exchange settings](https://learn.microsoft.com/en-us/graph/api/resources/exchangesettings?view=graph-rest-1.0). Get a list of Exchange settings, including mailboxes that belong to a user.

Export users' Windows settings and values stored in a cloud:

- Get a list of the user's [windowsSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0) objects.
- Get a filtered list of the user's [windowsSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0) objects by passing one of the following in the filter query:

  - [windowsSettingType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#windowssettingtype-values)
  - [windowsDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0#properties)

Manage work hours and location settings:

- Get and update a user's work hours and location preferences for scheduling and availability management.
- Access work plan recurrences and occurrences for flexible work arrangements.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). To learn how to get or update user settings, see [Get settings](https://learn.microsoft.com/en-us/graph/api/usersettings-get?view=graph-rest-1.0) and [Update settings](https://learn.microsoft.com/en-us/graph/api/usersettings-update?view=graph-rest-1.0).

This resource supports:

- Checking whether a user and the user's organization contribute to content discovery.
- Disabling or enabling content discovery for specific users. This also disables documents in Office Delve.

Note

This endpoint works only with users. You can't use this endpoint with contacts.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get settings](https://learn.microsoft.com/en-us/graph/api/usersettings-get?view=graph-rest-1.0) | [userSettings](https://learn.microsoft.com/en-us/graph/api/resources/usersettings?view=graph-rest-1.0) | Get the user and organization settings. |
| [Update settings](https://learn.microsoft.com/en-us/graph/api/usersettings-update?view=graph-rest-1.0) | [userSettings](https://learn.microsoft.com/en-us/graph/api/resources/usersettings?view=graph-rest-1.0) | Update the user current settings. |
| [List Exchange settings](https://learn.microsoft.com/en-us/graph/api/usersettings-list-exchange?view=graph-rest-1.0) | [exchangeSettings](https://learn.microsoft.com/en-us/graph/api/resources/exchangesettings?view=graph-rest-1.0) collection | Get a list of Exchange mailboxes that belong to a user. |
| [List Windows settings](https://learn.microsoft.com/en-us/graph/api/usersettings-list-windows?view=graph-rest-1.0) | [windowsSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0) collection | Get the **windowsSetting** objects and their properties for the signed in user. |
| [Get work hours and locations](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-get?view=graph-rest-1.0) | [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0) | Get the properties and relationships of a user's [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contributionToContentDiscoveryAsOrganizationDisabled | Boolean | Reflects the [organization level setting](https://support.office.com/en-us/article/office-delve-for-office-365-admins-54f87a42-15a4-44b4-9df0-d36287d9531b#bkmk_delveonoff) controlling delegate access to the [trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending) API. When set to true, the organization doesn't have access to Office Delve. The relevancy of the content displayed in Microsoft 365, for example in Suggested sites in SharePoint Home and the Discover view in OneDrive for work or school is affected for the whole organization. This setting is read-only and can only be changed by administrators in the [SharePoint admin center](https://support.office.com/article/about-the-office-365-admin-center-758befc4-0888-4009-9f14-0d147402fd23?ui=en-US&rs=en-US&ad=US). |
| contributionToContentDiscoveryDisabled | Boolean | When set to true, the delegate access to the user's [trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending) API is disabled. When set to true, documents in the user's Office Delve are disabled. When set to true, the relevancy of the content displayed in Microsoft 365, for example in Suggested sites in SharePoint Home and the Discover view in OneDrive for work or school is affected. Users can control this setting in [Office Delve](https://support.office.com/en-us/article/are-my-documents-safe-in-office-delve-f5f409a2-37ed-4452-8f61-681e5e1836f3?ui=en-US&rs=en-US&ad=US#bkmk_optout). |
| id | String | Unique identifier of the user setting. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| windows | [windowsSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0) collection | The Windows settings of the user stored in the cloud. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| exchange | [exchangeSettings](https://learn.microsoft.com/en-us/graph/api/resources/exchangesettings?view=graph-rest-1.0) | The Exchange settings for mailbox discovery. |
| itemInsights | [userInsightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/userinsightssettings?view=graph-rest-1.0) | The user's settings for the visibility of meeting hour insights, and insights derived between a user and other items in Microsoft 365, such as documents or sites. [Get userInsightsSettings](https://learn.microsoft.com/en-us/graph/api/userinsightssettings-get?view=graph-rest-1.0) through this navigation property. |
| windows | [windowsSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0) collection | The Windows settings of the user stored in the cloud. |
| workHoursAndLocations | [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0) | The user's settings for work hours and location preferences for scheduling and availability management. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contributionToContentDiscoveryDisabled": false,
  "contributionToContentDiscoveryAsOrganizationDisabled": false
}
```
