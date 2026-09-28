<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# communicationsUserIdentity resource type

Namespace: microsoft.graph

Represents the identity of a user present in [Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/) who participates in a communication; for example, as a caller in an audio-video call.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name associated with the user. Inherited from **identity**. |
| id | String | The user's object ID. Inherited from **identity**. |
| tenantId | String | The user's tenant ID. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)",
  "tenantId": "String"
}
```
