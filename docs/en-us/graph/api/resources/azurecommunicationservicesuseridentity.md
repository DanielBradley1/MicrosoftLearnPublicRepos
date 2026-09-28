<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azurecommunicationservicesuseridentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# azureCommunicationServicesUserIdentity resource type

Namespace: microsoft.graph

Represents the identity of a participant who joined the communication via Azure Communication Services.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureCommunicationServicesResourceId | String | The Azure Communication Services resource ID associated with the user. |
| displayName | String | The display name associated with the user. Inherited from **identity**. |
| id | String | The unique identifier for the user. Inherited from **identity**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "azureCommunicationServicesResourceId": "String",
  "displayName": "String",
  "id": "String (identifier)"
}
```
