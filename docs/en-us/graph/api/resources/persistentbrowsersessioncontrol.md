<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/persistentbrowsersessioncontrol?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# persistentBrowserSessionControl resource type

Namespace: microsoft.graph

Session control to define whether to persist cookies or not. Inherits from [Conditional Access Session Control](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrol?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Specifies whether the session control is enabled. |
| mode | persistentBrowserSessionMode | The possible values are: `always`, `never`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isEnabled": true,
  "mode": "String"
}
```
