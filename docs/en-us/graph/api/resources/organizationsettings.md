<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/organizationsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# organizationSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The `/organization/{organizationId}/settings/itemInsights` endpoint is deprecated and will stop returning data on May 1, 2024. Please use the new [peopleAdminSettings](https://learn.microsoft.com/en-us/graph/api/resources/peopleadminsettings) resource instead.

Contains settings that are applicable to the [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-beta) or that should be applied to [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) objects within an organization.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List contactInsights](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-contactinsights?view=graph-rest-beta) | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) | Get the properties of an [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) object for displaying or returning insights for the contacts of users in an organization. |
| [List microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-microsoftapplicationdataaccess?view=graph-rest-beta) | [microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta) | Get the properties of a [microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta) object that specify access from Microsoft applications to Microsoft 365 user data in an organization. |
| [List peopleInsights](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-peopleinsights?view=graph-rest-beta) | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) | Get the properties of an [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) object for displaying or returning people insights in an organization. |
| [List itemInsights](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-iteminsights?view=graph-rest-beta) \(deprecated\) | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) | Get the properties of an [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) object for displaying or returning item insights in an organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for an **organizationSettings** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the settings object for the organization. |
| contactInsights | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) | Contains the properties that are configured by an administrator as a tenant-level privacy control whether to identify duplicate contacts among a user's contacts list and suggest the user to merge those contacts to have a cleaner contacts list. [List contactInsights](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-contactinsights?view=graph-rest-beta) returns the *settings* to display or return contact insights in an organization. |
| microsoftApplicationDataAccessSettings | [microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta) | Contains the properties that are configured by an administrator to specify access from Microsoft applications to Microsoft 365 data belonging to users in an organization. [List microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-microsoftapplicationdataaccess?view=graph-rest-beta) returns the *settings* that specify the access. |
| peopleInsights | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) | Contains the properties that are configured by an administrator for the visibility of a list of people [relevant and working with](https://learn.microsoft.com/en-us/graph/people-insights-overview#including-a-person-as-relevant-or-working-with) a user in Microsoft 365. [List peopleInsights](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-peopleinsights?view=graph-rest-beta) returns the *settings* to display or return people insights in an organization. |
| itemInsights | [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-beta) \(deprecated\) | Contains the properties that are configured by an administrator for the visibility of Microsoft Graph-derived insights, between a user and other items in Microsoft 365, such as documents or sites. [List itemInsights](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-iteminsights?view=graph-rest-beta) returns the *settings* to display or return item insights in an organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)"
}
```
