<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# keyValue resource type

Namespace: microsoft.graph

Represents a key-value pair. This object is configured in the following resources:

- **attributeCollection** property of [contentCustomization](https://learn.microsoft.com/en-us/graph/api/resources/contentcustomization?view=graph-rest-1.0), which is used by [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0)
- **additionalDetails** property of [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | string | Key for the key-value pair. |
| value | string | Value for the key-value pair. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "key": "string",
  "value": "string"
}
```
