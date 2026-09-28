<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-displaytemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# displayTemplate resource type

Namespace: microsoft.graph.externalConnectors

Defines the appearance of the content and the conditions that dictate when the template should be displayed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The text identifier for the display template; for example, `contosoTickets`. Maximum 16 characters. Only alphanumeric characters allowed. |
| layout | [microsoft.graph.Json](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-json?view=graph-rest-1.0) | The definition of the content's appearance, represented by an [Adaptive Card](https://learn.microsoft.com/en-us/adaptive-cards/authoring-cards/getting-started), which is a JSON-serialized card object model. |
| priority | Int32 | Defines the priority of a display template. A display template with priority 1 is evaluated before a template with priority 4. Gaps in priority values are supported. Must be positive value. |
| rules | [microsoft.graph.externalConnectors.propertyRule](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-propertyrule?view=graph-rest-1.0) collection | Specifies additional rules for selecting this display template based on the item schema. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
    {
      "id": "String",
      "layout": {"type": "AdaptiveCard","version": "1.0","body": [{"type": "TextBlock","text": "String"}]},
      "priority": 0,
      "rules": [
        {
          "property": "String",
          "operation": "String",
          "valuesJoinedBy": "String",
          "values": [
              "String",
              "String"
          ]
        }
      ]      
    }
```
