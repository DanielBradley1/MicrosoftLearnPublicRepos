<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/listinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# listInfo resource type

Namespace: microsoft.graph

The **listInfo** complex type provides additional information about a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0).

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentTypesEnabled": false,
  "hidden": false,
  "template": "documentLibrary | genericList | tasks | survey | links | announcements | contacts | ..."
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **contentTypesEnabled** | Boolean | If `true`, indicates that content types are enabled for this list. |
| **hidden** | Boolean | If `true`, indicates that the list isn't normally visible in the SharePoint user experience. |
| **template** | String | An enumerated value that represents the base list template used in creating the list. Possible values include `documentLibrary`, `genericList`, `task`, `survey`, `announcements`, `contacts`, and more. |

### Remarks

While most lists created by users have one of the values listed above, other values are possible as well. Your app should be prepared to handle any values that aren't listed here. For developers familiar with SharePoint's CSOM APIs, the `template` value corresponds to the `SPListTemplateType` enumeration.
