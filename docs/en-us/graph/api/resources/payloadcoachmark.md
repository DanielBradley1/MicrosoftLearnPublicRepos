<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/payloadcoachmark?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# payloadCoachmark resource type

Namespace: microsoft.graph

Represents the payload coachmark detail of a payload. A coachmark is an indicator to educate users in learning how to verify the authenticity of the payload in an attack simulation training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| coachmarkLocation | [coachmarkLocation](https://learn.microsoft.com/en-us/graph/api/resources/coachmarklocation?view=graph-rest-1.0) | The coachmark location. |
| description | String | The description about the coachmark. |
| indicator | String | The coachmark indicator. |
| isValid | Boolean | Indicates whether the coachmark is valid or not. |
| language | String | The coachmark language. |
| order | String | The coachmark order. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.payloadCoachmark",
    "coachmarkLocation": {
        "@odata.type": "microsoft.graph.coachmarkLocation"
    },
    "description": "String",
    "indicator": "String",
    "isValid": "Boolean",
    "language": "String",
    "order": "String"
}
```
