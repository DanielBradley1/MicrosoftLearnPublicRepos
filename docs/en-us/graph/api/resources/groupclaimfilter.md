<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupclaimfilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# groupClaimFilter resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Applies filters to the group of the user to be included in the group claim. It can be a useful means of reducing the token size.

Inherits from [groupClaimFilterBase](https://learn.microsoft.com/en-us/graph/api/resources/groupclaimfilterbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| matchOn | matchOn | Identifies the group attribute on which the filter would be applied. The possible values are: `displayName`, `samAccountName`, `unknownFutureValue`. |
| type | filterType | Selects the type of filter you wish to apply to the attribute selected by the matchOn property. The possible values are: `prefix`, `suffix`, `contains`, `unknownFutureValue`. |
| value | String | The value of the filter to be applied. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.groupClaimFilter",
  "type": "String",
  "matchOn": "String",
  "value": "String"
}
```
