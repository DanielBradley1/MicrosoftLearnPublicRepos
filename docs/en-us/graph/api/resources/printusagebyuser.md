<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printusagebyuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# printUsageByUser resource type

Namespace: microsoft.graph

Describes print activity for a user during a specified time period \(usageDate\).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily reports by user](https://learn.microsoft.com/en-us/graph/api/reportroot-list-dailyprintusagebyuser?view=graph-rest-1.0) | [printUsageByUser](https://learn.microsoft.com/en-us/graph/api/resources/printusagebyuser?view=graph-rest-1.0) | Get a list of daily print usage summaries, grouped by user. |
| [List monthly reports by user](https://learn.microsoft.com/en-us/graph/api/reportroot-list-monthlyprintusagebyuser?view=graph-rest-1.0) | [printUsageByUser](https://learn.microsoft.com/en-us/graph/api/resources/printusagebyuser?view=graph-rest-1.0) | Get a list of monthly print usage summaries, grouped by user. |
| [Get](https://learn.microsoft.com/en-us/graph/api/printusagebyuser-get?view=graph-rest-1.0) | [printUsageByUser](https://learn.microsoft.com/en-us/graph/api/resources/printusagebyuser?view=graph-rest-1.0) | Read properties and relationships of a printUsageByUser object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blackAndWhitePageCount | Int64 | The estimated number of black and white pages printed on behalf of the user based on reporting by the printer. |
| colorPageCount | Int64 | The estimated number of color pages printed on behalf of the user based on reporting by the printer. |
| completedBlackAndWhiteJobCount | Int64 | The number of black and white print jobs completed on behalf of the user. |
| completedColorJobCount | Int64 | The number of color print jobs completed on behalf of the user. |
| completedJobCount | Int64 | The number of print jobs that were completed on behalf of the user. |
| doubleSidedSheetCount | Int64 | The estimated number of double-sided media sheets printed on behalf of the user based on reporting by the printer. |
| id | String | The ID of this usage summary. |
| incompleteJobCount | Int64 | The number of print jobs that were queued on behalf of the user, but not completed. |
| mediaSheetCount | Int64 | The estimated number of media sheets printed on behalf of the user based on reporting by the printer. |
| pageCount | Int64 | The estimated number of pages printed on behalf of the user based on reporting by the printer. |
| singleSidedSheetCount | Int64 | The estimated number of single-sided media sheets printed on behalf of the user based on reporting by the printer. |
| usageDate | Date | The date associated with these statistics. |
| userPrincipalName | String | The UPN of the user represented by these statistics. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "id": "String (identifier)",
    "userPrincipalName": "String (identifier)",
    "usageDate": "String (timestamp)",
    "completedBlackAndWhiteJobCount": "Integer",
    "completedColorJobCount": "Integer",
    "completedJobCount": "Integer",
    "incompleteJobCount": "Integer",
    "pageCount": "Integer",
    "blackAndWhitePageCount": "Integer",
    "colorPageCount": "Integer",
    "mediaSheetCount": "Integer",
    "doubleSidedSheetCount": "Integer",
    "singleSidedSheetCount": "Integer"
}
```
