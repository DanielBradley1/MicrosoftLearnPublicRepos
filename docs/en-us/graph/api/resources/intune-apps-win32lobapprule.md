<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppRule resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A base complex type to store the detection or requirement rule data for a Win32 LOB app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ruleType | [win32LobAppRuleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruletype?view=graph-rest-1.0) | The rule type indicating the purpose of the rule. The possible values are: `detection`, `requirement`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppRule",
  "ruleType": "String"
}
```
