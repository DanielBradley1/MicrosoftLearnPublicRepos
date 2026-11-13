<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/activitymetadata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# activityMetadata resource type

Namespace: microsoft.graph

Represents metadata about a specific user activity being evaluated, including the activity type and location.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | microsoft.graph.security.userActivityType | The type of user activity. Possible values are `uploadText`, `uploadFile`, `downloadText`, `downloadFile`, `unknownFutureValue`, `copyToClipboard`, `pasteFromClipboard`, `print`, `accessDebugTools`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `copyToClipboard`, `pasteFromClipboard`, `print`, `accessDebugTools`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.activityMetadata",
  "activity": "String",
}
```
