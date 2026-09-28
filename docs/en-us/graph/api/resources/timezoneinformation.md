<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timezoneinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# timeZoneInformation resource type

Namespace: microsoft.graph

Represents a time zone. The supported format is Windows, and [Internet Assigned Numbers Authority \(IANA\) time zone](https://www.iana.org/time-zones) \(also known as Olson time zone\) format as well when the current known problem is fixed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alias | string | An identifier for the time zone. |
| displayName | string | A display string that represents the time zone. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "alias": "string",
  "displayName": "string"
}
```
