<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# intelligenceProfileIndicator resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an indicator of threat or compromise related to the contents of an [intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0).

The relationship from an **intelligenceProfileIndicator** to an [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) provides the means for threat intelligence API users to further evaluate details about reported indicator.

Inherits from [microsoft.graph.security.indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get intelligence profile indicator](https://learn.microsoft.com/en-us/graph/api/security-intelligenceprofileindicator-get?view=graph-rest-1.0) | [microsoft.graph.security.intelligenceProfileIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.intelligenceProfileIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| firstSeenDateTime | DateTimeOffset | Designate when an artifact was first used actively in an attack, when a particular sample was compiled, or if neither of those could be ascertained when the file was first seen in public repositories \(for example, VirusTotal, ANY.RUN, Hybrid Analysis\) or reported publicly. |
| id | String | A system generated ID for this **intelligenceProfileIndicator**. Inherited from [microsoft.graph.security.indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | Designate when an artifact was most recently used actively in an attack, when a particular sample was compiled, or if neither of those could be ascertained when the file was first seen in public repositories \(for example, VirusTotal, ANY.RUN, Hybrid Analysis\) or reported publicly. |
| source | microsoft.graph.security.indicatorSource | Communicates the source of this **intelligenceProfileIndicator**. Inherited from [microsoft.graph.security.indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0). The possible values are: `microsoft`, `osint`, `public`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| artifact | [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) | The [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) that is reported in this **intelligenceProfileIndicator**. Inherited from [microsoft.graph.security.indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.intelligenceProfileIndicator",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "source": "String"
}
```
