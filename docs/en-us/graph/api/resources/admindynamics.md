<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# adminDynamics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Company-wide configuration for Microsoft Dynamics 365.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/admindynamics-get?view=graph-rest-beta) | [adminDynamics](https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta) | Read the properties and relationships of a [adminDynamics](https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/admindynamics-update?view=graph-rest-beta) | [adminDynamics](https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta) | Update the properties and relationships of a [adminDynamics](https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customerVoice | [customerVoiceSettings](https://learn.microsoft.com/en-us/graph/api/resources/customervoicesettings?view=graph-rest-beta) | Company-wide settings for Microsoft Dynamics 365 Customer Voice. |
| id | String | Unique ID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adminDynamics",
  "id": "String (identifier)",
  "customerVoice": {
    "@odata.type": "customerVoiceSettings"
  }
}
```
