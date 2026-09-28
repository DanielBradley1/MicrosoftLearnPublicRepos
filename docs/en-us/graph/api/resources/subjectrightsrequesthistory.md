<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# subjectRightsRequestHistory resource type

Namespace: microsoft.graph

Represents the history for a subject rights request.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user who changed the subject rights request. |
| eventDateTime | DateTimeOffset | Data and time when the entity was changed. |
| stage | [subjectRightsRequestStage](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststage?view=graph-rest-1.0) | The stage when the entity was changed. |
| stageStatus | subjectRightsRequestStageStatus | The status of the stage when the entity was changed. The possible values are: `notStarted`, `current`, `completed`, `failed`, `unknownFutureValue`. |
| type | String | Type of history. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subjectRightsRequestHistory",
    "type": "String",
    "stage": "String",
    "stageStatus": "String",
    "eventDateTime": "String (timeStamp)",
    "changedBy": {
        "user": {
            "id": "String",
            "displayName": "String"
        }
    }
}
```
