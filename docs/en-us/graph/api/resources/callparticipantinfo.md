<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callparticipantinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# callParticipantInfo resource type

Namespace: microsoft.graph

Represents the details for a call participant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| participant | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the call participant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callParticipantInfo",
  "participant": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```
