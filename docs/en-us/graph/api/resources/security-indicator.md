<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-06 -->

# indicator resource type

Namespace: microsoft.graph.security

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR or Microsoft Sentinel license. No separate license is required to access these APIs.

An abstract type that represents an indicator of compromise or increased risk. Indicators communicate artifacts that indicate that an asset was affected by or related to an attack vector or malicious actor.

This resource isn't directly addressable. You can interact with this resource through one of the following subtypes:

- [articleIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-articleindicator?view=graph-rest-1.0)
- [intelligenceProfileIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The system-generated ID for the **indicator**. |
| source | microsoft.graph.security.indicatorSource | The source that provides this **indicator**. The possible values are: `microsoftDefenderThreatIntelligence`, `openSourceIntelligence`, `public`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| artifact | [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) | The artifact related to this **indicator**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.indicator",
  "id": "String (identifier)",
  "source": "String"
}
```
