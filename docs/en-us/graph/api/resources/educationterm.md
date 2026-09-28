<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationterm?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# educationTerm resource type

Namespace: microsoft.graph

A term. This represents a designated portion of the academic year. It's used within [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the term. |
| endDate | Date | End of the term. |
| externalId | String | ID of term in the syncing system. |
| startDate | Date | Start of the term. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationTerm",
  "displayName": "String",
  "endDate": "Date",
  "externalId": "String",
  "startDate": "Date"
}
```
