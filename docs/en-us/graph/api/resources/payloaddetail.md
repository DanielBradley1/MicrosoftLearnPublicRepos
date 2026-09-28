<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-16 -->

# payloadDetail resource type

Namespace: microsoft.graph

Represents details about a payload.

Base type of [emailPayloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/emailpayloaddetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| coachMarks | [payloadCoachmark](https://learn.microsoft.com/en-us/graph/api/resources/payloadcoachmark?view=graph-rest-1.0) collection | Payload coachmark details. |
| content | String | Payload content details. |
| phishingUrl | String | The phishing URL used to target a user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.payloadDetail",
    "coachMarks": [
        {
            "@odata.type": "microsoft.graph.payloadCoachmark"
        }
    ],
    "content": "String",
    "phishingUrl": "String"
}
```
