<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printusagebyprinter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# printUsageByPrinter resource type

Namespace: microsoft.graph

Describes print activity for a printer during a specified time period \(usageDate\).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily reports by printer](https://learn.microsoft.com/en-us/graph/api/reportroot-list-dailyprintusagebyprinter?view=graph-rest-1.0) | printUsageByPrinter | Get a list of daily print usage summaries, grouped by printer. |
| [List monthly reports by printer](https://learn.microsoft.com/en-us/graph/api/reportroot-list-monthlyprintusagebyprinter?view=graph-rest-1.0) | printUsageByPrinter | Get a list of monthly print usage summaries, grouped by printer. |
| [Get](https://learn.microsoft.com/en-us/graph/api/printusagebyprinter-get?view=graph-rest-1.0) | printUsageByPrinter | Read the properties and relationships of a printUsageByPrinter object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blackAndWhitePageCount | Int64 | The estimated number of black and white pages printed based on reporting by the printer. |
| colorPageCount | Int64 | The estimated number of color pages printed based on reporting by the printer. |
| completedBlackAndWhiteJobCount | Int64 | The number of black and white print jobs completed by the printer. |
| completedColorJobCount | Int64 | The number of color print jobs completed by the printer. |
| completedJobCount | Int64 | The number of print jobs that were completed by the printer. |
| doubleSidedSheetCount | Int64 | The estimated number of double-sided media sheets printed based on reporting by the printer. |
| id | String | The ID of this usage summary. |
| incompleteJobCount | Int64 | The number of print jobs that were queued for the printer, but not completed. |
| mediaSheetCount | Int64 | The estimated number of media sheets printed based on reporting by the printer. |
| pageCount | Int64 | The estimated number of pages printed based on reporting by the printer. |
| printerId | String | The ID of the printer represented by these statistics. |
| printerName | String | The name of the printer represented by these statistics. |
| singleSidedSheetCount | Int64 | The estimated number of single-sided media sheets printed based on reporting by the printer. |
| usageDate | Date | The date associated with these statistics. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printUsageByPrinter",
  "id": "String (identifier)",
  "printerId": "String",
  "printerName": "String (identifier)",
  "usageDate": "Date",
  "completedBlackAndWhiteJobCount": "Integer",
  "completedColorJobCount": "Integer",
  "incompleteJobCount": "Integer",
  "completedJobCount": "Integer",
  "pageCount": "Integer",
  "blackAndWhitePageCount": "Integer",
  "colorPageCount": "Integer",
  "mediaSheetCount": "Integer",
  "doubleSidedSheetCount": "Integer",
  "singleSidedSheetCount": "Integer"
}
```
