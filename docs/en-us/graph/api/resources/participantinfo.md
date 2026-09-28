<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/participantinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# participantInfo resource type

Namespace: microsoft.graph

Contains additional properties about the participant identity

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| countryCode | String | The ISO 3166-1 Alpha-2 country code of the participant's best estimated physical location at the start of the call. Read-only. |
| endpointType | String | The type of endpoint the participant is using. The possible values are: `default`, `skypeForBusiness`, or `skypeForBusinessVoipPhone`. Read-only. |
| identity | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) associated with this participant. Read-only. |
| languageId | String | The language culture string. Read-only. |
| participantId | String | The participant ID of the participant. Read-only. |
| region | String | The home region of the participant. This can be a country, a continent, or a larger geographic region. This doesn't change based on the participant's current physical location. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "countryCode": "String",
  "identity": { "@odata.type": "#microsoft.graph.identitySet" },
  "endpointType": "default | skypeForBusiness | skypeForBusinessVoipPhone",
  "languageId": "String",
  "region": "String",
  "participantId": "String"
}
```
