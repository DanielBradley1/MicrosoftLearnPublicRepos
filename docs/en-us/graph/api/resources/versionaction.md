<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/versionaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# versionAction resource type

Namespace: microsoft.graph

The presence of the **versionAction** resource on an [**itemActivity**](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) indicates that the activity caused a new version to be created.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| newVersion | string | The name of the new version that was created by this action. |

## JSON representation

```json
{
  "newVersion": "string"
}
```
