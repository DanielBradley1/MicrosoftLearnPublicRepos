<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/namepronunciationsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-29 -->

# namePronunciationSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a setting to control people-related admin settings in the tenant.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/namepronunciationsettings-get?view=graph-rest-beta) | [namePronunciationSettings](https://learn.microsoft.com/en-us/graph/api/resources/namepronunciationsettings?view=graph-rest-beta) | Read the properties and relationships of a [namePronunciationSettings](https://learn.microsoft.com/en-us/graph/api/resources/namepronunciationsettings?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/namepronunciationsettings-update?view=graph-rest-beta) | [namePronunciationSettings](https://learn.microsoft.com/en-us/graph/api/resources/namepronunciationsettings?view=graph-rest-beta) | Update the properties of a [namePronunciationSettings](https://learn.microsoft.com/en-us/graph/api/resources/namepronunciationsettings?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the **namePronunciationSettings** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabledInOrganization | Boolean | `true` to enable name pronunciation in the organization; otherwise, `false`. The default value is `false`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.namePronunciationSettings",
  "id": "String (identifier)",
  "isEnabledInOrganization": "Boolean"
}
```
