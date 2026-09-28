<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookoperationerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# workbookOperationError resource type

Represents an error from a failed workbook operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error code. |
| innererror | error object | Optional. Other error objects that may be more specific than the top level error. |
| message | String | The error message. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "innererror": { "@odata.type": "odata.error" },
  "message": "String"
}
```
