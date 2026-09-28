<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restorepointsearchresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# restorePointSearchResponse resource type

Namespace: microsoft.graph

Contains a collection of protection units for which no [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) is found and a collection of restore points for the [protectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) objects with a protection history in the specified time period.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| noResultProtectionUnitIds | String collection | Contains alist of protection units with no restore points. |
| searchResponseId | String | The unique identifier of the search response. |
| searchResults | [restorePointSearchResult](https://learn.microsoft.com/en-us/graph/api/resources/restorepointsearchresult?view=graph-rest-1.0) collection | Contains a collection of restore points. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restorePointSearchResponse",
  "searchResponseId": "String",
  "searchResults": [
    {
      "@odata.type": "microsoft.graph.restorePointSearchResult"
    }
  ],
  "noResultProtectionUnitIds": [
    "String"
  ]
}
```
