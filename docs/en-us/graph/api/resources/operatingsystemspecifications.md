<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/operatingsystemspecifications?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# operatingSystemSpecifications resource type

Namespace: microsoft.graph

Contains the platform and version details of the operating system.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operatingSystemPlatform | String | The platform of the operating system \(for example, "Windows"\). |
| operatingSystemVersion | String | The version string of the operating system. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.operatingSystemSpecifications",
  "operatingSystemPlatform": "String",
  "operatingSystemVersion": "String"
}
```
