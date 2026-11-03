<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/solutionsroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# solutionsRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The entry point for [Microsoft Bookings](https://learn.microsoft.com/en-us/graph/api/resources/booking-api-overview?view=graph-rest-beta), [virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-beta), [business scenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario-overview?view=graph-rest-beta), and [SharePoint migration](https://learn.microsoft.com/en-us/graph/api/resources/sharepointroot?view=graph-rest-beta) APIs.

All Microsoft Graph calls to resources under `/solutions` use the following service root URL:

```http
https://graph.microsoft.com/{version}/solutions/
```

To access Bookings businesses, use the following syntax:

```http
https://graph.microsoft.com/{version}/solutions/bookingBusinesses 
```

To access Bookings currencies, use the following syntax:

```http
https://graph.microsoft.com/{version}/solutions/bookingCurrencies 
```

To access business scenarios, use the following syntax:

```http
https://graph.microsoft.com/{version}/solutions/businessScenarios 
```

To access virtual event webinars, use the following syntax:

```http
https://graph.microsoft.com/{version}/solutions/virtualEvents/webinars
```

To access virtual event town halls, use the following syntax:

```http
https://graph.microsoft.com/{version}/solutions/virtualEvents/townhalls
```

To access approval items, use the following syntax:

```http
https://graph.microsoft.com/{version}/solutions/approval/approvalItems
```

To access SharePoint cross-organization migration mappings, use the following syntax:

```http
https://graph.microsoft.com/{version}/solutions/sharePoint/migrations/crossOrganizationGroupMappings
https://graph.microsoft.com/{version}/solutions/sharePoint/migrations/crossOrganizationUserMappings
```

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| approvalItems | [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta) collection | A collection of approval items. |
| bookingBusinesses | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-beta) collection | A collection of businesses in Microsoft Bookings. Read-only. Nullable. |
| bookingCurrencies | [bookingCurrency](https://learn.microsoft.com/en-us/graph/api/resources/bookingcurrency?view=graph-rest-beta) collection | A collection of monetary currencies supported by a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-beta). Read-only. Nullable. |
| businessScenarios | [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) collection | A collection of scenarios that contain relevant data and configuration information for a specific problem domain. |
| sharePoint | [sharePointRoot](https://learn.microsoft.com/en-us/graph/api/resources/sharepointroot?view=graph-rest-beta) | Container for SharePoint resources that include cross-organization migration operations. |
| virtualEvents | [virtualEventsRoot](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsroot?view=graph-rest-beta) collection | A collection of virtual events. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.solutionsRoot"
}
```
