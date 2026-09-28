<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-articleindicator?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# articleIndicator resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a resource that communicates indicators of threat or compromise related to the contents of an [article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0).

The relationship from an **articleIndicator** to an [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) provides the means for threat intelligence API users to further evaluate details about reported indicator.

Inherits from [indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get article indicator](https://learn.microsoft.com/en-us/graph/api/security-articleindicator-get?view=graph-rest-1.0) | [microsoft.graph.security.articleIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-articleindicator?view=graph-rest-1.0) | Read the properties and relationships of a [articleIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-articleindicator?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The system-generated ID for the **articleIndicator**. Inherited from [microsoft.graph.security.indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0). |
| source | microsoft.graph.security.indicatorSource | Communicates where this **articleIndicator** originated. The possible values are: `microsoft`, `osint`, `public`, `unknownFutureValue`. Inherited from [microsoft.graph.security.indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| artifact | [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) | The [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) that is reported in this **articleIndicator**. Inherited from [microsoft.graph.security.indicator](https://learn.microsoft.com/en-us/graph/api/resources/security-indicator?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.articleIndicator",
  "id": "String (identifier)",
  "source": "String"
}
```
