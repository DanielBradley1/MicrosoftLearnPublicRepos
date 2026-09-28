<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# yearTimePeriodDefinition resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents annual time periods such as academic or fiscal years. This resource allows the association of incoming data to a year to help build historical data, day-by-day, year-over-year, as time progresses. In the case of data domain for education rostering, this is commonly referred to as an academic year. The approach is aligned to an academic year versus a calendar year.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/industrydata-yeartimeperioddefinition-post?view=graph-rest-beta) | [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) | Create a new [yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-yeartimeperioddefinition-list?view=graph-rest-beta) | [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) collection | Get a list of the [yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-yeartimeperioddefinition-get?view=graph-rest-beta) | [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) | Read the properties and relationships of a [yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-yeartimeperioddefinition-update?view=graph-rest-beta) | [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) | Update the properties of a [yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-yeartimeperioddefinition-delete?view=graph-rest-beta) | None | Delete a [yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the year. Maximum supported length is 100 characters. |
| endDate | Date | The last day of the year using ISO 8601 format for date. |
| startDate | Date | The first day of the year using ISO 8601 format for date. |
| year | [microsoft.graph.industryData.yearReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yearreferencevalue?view=graph-rest-beta) | A pointer to a year entry in the [referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) collection. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.yearTimePeriodDefinition",
  "displayName": "String",
  "endDate": "String (date)",
  "startDate": "String (date)",
  "year": {
    "@odata.type": "microsoft.graph.industryData.yearReferenceValue"
  }
}
```
