<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-monitoringsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# monitoringSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Settings controlling automated monitoring and response in a deployment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| monitoringRules | [microsoft.graph.windowsUpdates.monitoringRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-monitoringrule?view=graph-rest-beta) collection | Specifies the rules through which monitoring signals can trigger actions on the deployment. Rules are combined using "or." |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.monitoringSettings",
  "monitoringRules": [
    {
      "@odata.type": "microsoft.graph.windowsUpdates.monitoringRule"
    }
  ]
}
```
