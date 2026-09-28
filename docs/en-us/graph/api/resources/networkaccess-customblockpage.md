<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-customblockpage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-22 -->

# customBlockPage resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the end user message when Global Secure Access blocks end users from accessing a resource on the web.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-customblockpage-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.customBlockPage](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-customblockpage?view=graph-rest-beta) | Get [microsoft.graph.networkaccess.customBlockPage](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-customblockpage?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-customblockpage-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.customBlockPage](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-customblockpage?view=graph-rest-beta) | Update [microsoft.graph.networkaccess.customBlockPage](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-customblockpage?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| state | microsoft.graph.networkaccess.status | When state is enabled, the custom block page is shown to end users who are blocked from accessing a resource on the web. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| configuration | [microsoft.graph.networkaccess.blockPageConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-blockpageconfigurationbase?view=graph-rest-beta) | The current configuration of the customized message. The body can be input in limited markdown language, supporting links via the format: `[link](https://example.com)`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.customBlockPage",
  "id": "String (identifier)",
  "state": "String",
  "configuration": {
    "@odata.type": "microsoft.graph.networkaccess.blockPageConfigurationBase"
  }
}
```
