<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/regionalformatoverrides?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# regionalFormatOverrides resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A collection of strings representing formatting overrides for calendars, dates, and times.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| calendar | String | The calendar to use; for example, Gregorian Calendar.  <br>  <br>Returned by default. |
| firstDayOfWeek | microsoft.graph.dayOfWeek | The first day of the week to use; for example, Sunday.  <br>  <br>Returned by default. |
| shortDateFormat | String | The short date time format to be used for displaying dates.  <br>  <br>Returned by default. |
| longDateFormat | String | The long date time format to be used for displaying dates.  <br>  <br>Returned by default. |
| shortTimeFormat | String | The short time format to be used for displaying time.  <br>  <br>Returned by default. |
| longTimeFormat | String | The long time format to be used for displaying time.  <br>  <br>Returned by default. |
| timeZone | String | The timezone to be used for displaying time.  <br>  <br>Returned by default. |

## Relationships

None.

## JSON representation

The following is a JSON definition of the resource.

```json
{
    "calendar": "string",
    "firstDayOfWeek": "string",
    "shortDateFormat": "string",
    "longDateFormat": "string",
    "shortTimeFormat": "string",
    "longTimeFormat": "string",
    "timeZone": "string"
}
```
