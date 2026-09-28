<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# threatIntelligencePolicySettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configurable settings that define how a [threat intelligence policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) operates. These settings control the default action to take when a threat is detected.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultAction | microsoft.graph.networkaccess.threatIntelligenceAction | The default action to take when a threat is detected by the policy. This action applies when no specific rule action overrides it. The possible values are: `allow`, `block`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligencePolicySettings",
  "defaultAction": "String"
}
```
