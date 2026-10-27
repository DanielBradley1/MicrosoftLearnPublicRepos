<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/stringdictionary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# stringDictionary resource type

Namespace: microsoft.graph

Represents a set of custom properties that have string keys and string values. Each property name is a string key, and each property value must be a string or `null`. A `null` value is used only when you update a dictionary entry to remove it.

The [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) resource uses this type for its **customProperties** property.

Inherits from [dictionary](https://learn.microsoft.com/en-us/graph/api/resources/dictionary?view=graph-rest-1.0).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.stringDictionary"
}
```
