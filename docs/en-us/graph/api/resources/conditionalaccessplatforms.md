<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessplatforms?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# conditionalAccessPlatforms resource type

Namespace: microsoft.graph

Platforms included in and excluded from the policy scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludePlatforms | conditionalAccessDevicePlatform collection | The possible values are: `android`, `iOS`, `windows`, `windowsPhone`, `macOS`, `linux`, `all`, `unknownFutureValue`. |
| includePlatforms | conditionalAccessDevicePlatform collection | The possible values are: `android`, `iOS`, `windows`, `windowsPhone`, `macOS`, `linux`, `all`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "excludePlatforms": ["String"],
  "includePlatforms": ["String"]
}
```
