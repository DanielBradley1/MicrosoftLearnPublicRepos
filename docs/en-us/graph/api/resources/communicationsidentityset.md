<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/communicationsidentityset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-28 -->

# communicationsIdentitySet resource type

Namespace: microsoft.graph

Represents a combination of user and application identities that together identify a participant in a call or meeting.

Inherits from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [communicationsApplicationIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsapplicationidentity?view=graph-rest-1.0) | The application associated with this action. Inherited from **identitySet**. |
| applicationInstance | [communicationsApplicationInstanceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsapplicationinstanceidentity?view=graph-rest-1.0) | The application instance associated with this action. |
| assertedIdentity | [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) or [communicationsPhoneIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsphoneidentity?view=graph-rest-1.0) | An **identity** the participant would like to present itself as to the other participants in the call. |
| azureCommunicationServicesUser | [azureCommunicationServicesUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/azurecommunicationservicesuseridentity?view=graph-rest-1.0) | The Azure Communication Services user associated with this action. |
| encrypted | [communicationsEncryptedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsencryptedidentity?view=graph-rest-1.0) | The encrypted user associated with this action. |
| endpointType | endpointType | Type of endpoint that the participant uses. The possible values are: `default`, `voicemail`, `skypeForBusiness`, `skypeForBusinessVoipPhone`, `unknownFutureValue`. |
| guest | [communicationsGuestIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsguestidentity?view=graph-rest-1.0) | The guest user associated with this action. |
| onPremises | [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) | The Skype for Business on-premises user associated with this action. |
| phone | [communicationsPhoneIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsphoneidentity?view=graph-rest-1.0) | The phone user associated with this action. |
| user | [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) | The user associated with this action. Inherited from **identitySet**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "application": {"@odata.type": "microsoft.graph.communicationsApplicationIdentity"},
  "applicationInstance": {"@odata.type": "microsoft.graph.communicationsApplicationInstanceIdentity"},
  "assertedIdentity": {"@odata.type": "microsoft.graph.identity"},
  "azureCommunicationServicesUser": {"@odata.type": "microsoft.graph.azureCommunicationServicesUserIdentity"},
  "encrypted": {"@odata.type": "microsoft.graph.communicationsEncryptedIdentity"},
  "endpointType": "String",
  "guest": {"@odata.type": "microsoft.graph.communicationsGuestIdentity"},
  "onPremises": {"@odata.type": "microsoft.graph.communicationsUserIdentity"},
  "phone": {"@odata.type": "microsoft.graph.communicationsPhoneIdentity"},
  "user": {"@odata.type": "microsoft.graph.communicationsUserIdentity"}
}
```
