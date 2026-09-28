<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/stringdictionary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# stringDictionary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a set of custom properties that have string keys and string values. The [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-beta) resource uses this type for its **customProperties** property.

Inherits from [dictionary](https://learn.microsoft.com/en-us/graph/api/resources/dictionary?view=graph-rest-beta).

## Properties

A **stringDictionary** contains a dynamic set of properties. Each property name is a string key, and each property value must be a string or `null`. A `null` value is used only when updating a dictionary entry to remove it.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "String": "String"
}
```
