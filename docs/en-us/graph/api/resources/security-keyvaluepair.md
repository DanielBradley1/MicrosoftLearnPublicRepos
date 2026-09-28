<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# keyValuePair resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a key-value pair for sensitivity labels in Microsoft Purview Information Protection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name for this key-value pair. |
| value | String | Value for this key-value pair. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.keyValuePair",
  "name": "String",
  "value": "String"
}
```
