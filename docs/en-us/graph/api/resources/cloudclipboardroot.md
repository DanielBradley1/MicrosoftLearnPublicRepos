<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudclipboardroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# cloudClipboardRoot resource type

Namespace: microsoft.graph

Represents the information and properties of a cloudClipboardRoot and serves as an entry point for [cloudClipboardItem](https://learn.microsoft.com/en-us/graph/api/resources/cloudclipboarditem?view=graph-rest-1.0) objects.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/cloudclipboardroot-list-items?view=graph-rest-1.0) | [cloudClipboardItem](https://learn.microsoft.com/en-us/graph/api/resources/cloudclipboarditem?view=graph-rest-1.0) collection | Get a list of the **cloudClipboard** items and their properties. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| items | [cloudClipboardItem](https://learn.microsoft.com/en-us/graph/api/resources/cloudclipboarditem?view=graph-rest-1.0) collection | Represents a collection of Cloud Clipboard items. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudClipboardRoot"
}
```
