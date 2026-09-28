<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-searchsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# searchSettings resource type

Namespace: microsoft.graph.externalConnectors

Collects all configurable settings related to search over connector content.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| searchResultTemplates | [microsoft.graph.externalConnectors.displayTemplate](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-displaytemplate?view=graph-rest-1.0) collection | Enables the developer to define the appearance of the content and configure conditions that dictate when the template should be displayed. Maximum of 2 search result templates per connection. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "searchResultTemplates": [
    {
      "id": "String (identifier)",
      "rules": [
        {
          "property": "itemTitle",
          "operation": "contains",
          "valuesJoinedBy": "or",
          "values": [
              "contoso",
              "smart"
          ]
        }
      ],
      "layout": {"type": "AdaptiveCard","version": "1.0","body": [{"type": "TextBlock","text": "A contoso ticket."}]},
      "priority": 0
    },
    {
      "id": "String (identifier)",
      "rules": [
        {
          "property": "itemDescription",
          "operation": "contains",
          "valuesJoinedBy": "and",
          "values": [
              "contoso",
              "ticket"
          ]
        }
      ],
      "layout": {"type": "AdaptiveCard","version": "1.0","body": [{"type": "TextBlock","text": "A contoso ticket."}]},
      "priority": 1
    }
  ]
}
```
