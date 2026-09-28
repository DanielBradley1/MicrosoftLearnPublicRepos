<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emailpayloaddetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-15 -->

# emailPayloadDetail resource type

Namespace: microsoft.graph

Represents details of an email type payload.

Inherits from [payloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| coachmarks | [payloadCoachmark](https://learn.microsoft.com/en-us/graph/api/resources/payloadcoachmark?view=graph-rest-1.0) | Payload coachmark details. Inherited from [payloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0). |
| content | String | Payload content details. Inherited from [payloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0). |
| fromEmail | String | Email address of the user. |
| fromName | String | Display name of the user. |
| isExternalSender | Boolean | Indicates whether the sender isn't from the user's organization. |
| phishingUrl | String | Phishing URL used to target a user. Inherited from [payloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0). |
| subject | String | The subject of the email address sent to the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.emailPayloadDetail",
    "coachMarks": [
        {
            "@odata.type": "microsoft.graph.payloadCoachmark"
        }
    ],
    "content": "String",
    "fromEmail": "String",
    "fromName": "String",
    "isExternalSender": "Boolean",
    "phishingUrl": "String",
    "subject": "String"
}
```
