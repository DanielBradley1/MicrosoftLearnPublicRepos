<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-01 -->

# payload resource type

Namespace: microsoft.graph

Represents an attack simulation training payload in a tenant. A payload is the content \(for example, message, links, and attachments\) in a phishing email that is presented to users in an attack simulation training campaign.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-payloads?view=graph-rest-1.0) | [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) collection | Get a list of attack simulation payload for a tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/payload-get?view=graph-rest-1.0) | [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) | Get an attack simulation payload for a tenant. |
| [Get payload detail](https://learn.microsoft.com/en-us/graph/api/payloaddetail-get?view=graph-rest-1.0) | [payloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0) | Get an attack simulation campaign payload detail for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| brand | [payloadBrand](#payloadbrand-values) | The branch of a payload. The possible values are: `unknown`, `other`, `americanExpress`, `capitalOne`, `dhl`, `docuSign`, `dropbox`, `facebook`, `firstAmerican`, `microsoft`, `netflix`, `scotiabank`, `sendGrid`, `stewartTitle`, `tesco`, `wellsFargo`, `syrinxCloud`, `adobe`, `teams`, `zoom`, `unknownFutureValue`. |
| complexity | [payloadComplexity](#payloadcomplexity-values) | The complexity of a payload. The possible values are: `unknown`, `low`, `medium`, `high`, `unknownFutureValue`. |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the attack simulation and training campaign payload. |
| createdDateTime | DateTimeOffset | Date and time when the attack simulation and training campaign payload. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Description of the attack simulation and training campaign payload. |
| detail | [payloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0) | Additional details about the payload. |
| displayName | String | Display name of the attack simulation and training campaign payload. Supports `$filter` and `$orderby`. |
| id | String | Unique identifier for the attack simulation and training campaign payload. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| industry | [payloadIndustry](#payloadindustry-values) | Industry of a payload. The possible values are: `unknown`, `other`, `banking`, `businessServices`, `consumerServices`, `education`, `energy`, `construction`, `consulting`, `financialServices`, `government`, `hospitality`, `insurance`, `legal`, `courierServices`, `IT`, `healthcare`, `manufacturing`, `retail`, `telecom`, `realEstate`, `unknownFutureValue`. |
| isAutomated | Boolean | Indicates whether the attack simulation and training campaign payload was created from an automation flow. Supports `$filter` and `$orderby`. |
| isControversial | Boolean | Indicates whether the payload is controversial. |
| isCurrentEvent | Boolean | Indicates whether the payload is from any recent event. |
| language | String | Payload language. |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who most recently modified the attack simulation and training campaign payload. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the attack simulation and training campaign payload was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| payloadTags | String collection | Free text tags for a payload. |
| platform | payloadDeliveryPlatform | The payload delivery platform for a simulation. The possible values are: `unknown`, `sms`, `email`, `teams`, `unknownFutureValue`. |
| predictedCompromiseRate | Double | Predicted probability for a payload to phish a targeted user. |
| simulationAttackType | [simulationAttackType](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationattacktype-values) | Attack type of the attack simulation and training campaign. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `social`, `cloud`, `endpoint`, `unknownFutureValue`. |
| source | [simulationContentSource](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentsource-values) | Simulation content source. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `global`, `tenant`, `unknownFutureValue`. |
| status | [simulationContentStatus](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentstatus-values) | Simulation content status. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `draft`, `ready`, `archive`, `delete`, `unknownFutureValue`. |
| technique | [simulationAttackTechnique](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationattacktechnique-values) | The social engineering technique used in the attack simulation and training campaign. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `credentialHarvesting`, `attachmentMalware`, `driveByUrl`, `linkInAttachment`, `linkToMalwareFile`, `unknownFutureValue`, `oAuthConsentGrant`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `oAuthConsentGrant`. For more information on the types of social engineering attack techniques, see [simulations](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations). |
| theme | [payloadTheme](#payloadtheme-values) | The theme of a payload. The possible values are: `unknown`, `other`, `accountActivation`, `accountVerification`, `billing`, `cleanUpMail`, `controversial`, `documentReceived`, `expense`, `fax`, `financeReport`, `incomingMessages`, `invoice`, `itemReceived`, `loginAlert`, `mailReceived`, `password`, `payment`, `payroll`, `personalizedOffer`, `quarantine`, `remoteWork`, `reviewMessage`, `securityUpdate`, `serviceSuspended`, `signatureRequired`, `upgradeMailboxStorage`, `verifyMailbox`, `voicemail`, `advertisement`, `employeeEngagement`, `unknownFutureValue`. |

### payloadTheme values

| Member | Description |
| :--- | :--- |
| unknown | The payload theme is not defined. |
| other | The payload is other. |
| accountActivation | Payload theme is of account activation. |
| accountVerification | Payload theme is of account verification. |
| billing | Payload theme is of billing type. |
| cleanUpMail | Payload mail cleanup details. |
| controversial | Payload controversial information. |
| documentReceived | Payload tells that the document has been received. |
| expense | Payload contains expense-related details. |
| fax | Payload contains fax-specific details. |
| financeReport | Payload contains a finance report. |
| incomingMessages | Payload contains details about incoming messages. |
| invoice | Payload contains invoice details. |
| itemReceived | Payload contains details about an item received. |
| loginAlert | Payload contains login alert information. |
| mailReceived | Payload contains information about a mail received. |
| password | Payload with password details. |
| payment | Payload with payment details. |
| payroll | Payload with payroll-specific details. |
| personalizedOffer | Payload with details about a personalized offer. |
| quarantine | Payload with quarantine-related details. |
| remoteWork | Payload related to as remote work. |
| reviewMessage | Payload with a review message request. |
| securityUpdate | Payload mentions that a security update is required. |
| serviceSuspended | Payload mentions that a service has been suspended. |
| signatureRequired | Payload tells that a signature is required. |
| upgradeMailboxStorage | Payload asks to upgrade the mailbox storage. |
| verifyMailbox | Payload asks for mailbox verification. |
| voicemail | Payload with voicemail details. |
| advertisement | Payload with advertisement details. |
| employeeEngagement | Payload with employee engagement details. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

### payloadBrand values

| Member | Description |
| :--- | :--- |
| unknown | Payload brand as unknown. |
| other | Payload brand as other. |
| americanExpress | Payload brand as American Express. |
| capitalOne | Payload brand as Capital One. |
| dhl | Payload brand as DHL. |
| docuSign | Payload brand as DocuSign. |
| dropbox | Payload brand as Dropbox. |
| facebook | Payload brand as Facebook. |
| firstAmerican | Payload brand as First American. |
| microsoft | Payload brand as Microsoft. |
| netflix | Payload brand as Netflix. |
| scotiabank | Payload brand as Scotiabank. |
| sendGrid | Payload brand as SendGrid. |
| stewartTitle | Payload brand as Stewart Title. |
| tesco | Payload brand as Tesco. |
| wellsFargo | Payload brand as Wells Fargo. |
| syrinxCloud | Payload brand as Syrinx Cloud. |
| adobe | Payload brand as Adobe. |
| teams | Payload brand as Teams. |
| zoom | Payload brand as Zoom. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

### payloadIndustry values

| Member | Description |
| :--- | :--- |
| unknown | Payload industry as unknown. |
| other | Payload industry as other. |
| banking | Payload industry as banking. |
| businessServices | Payload industry as business services. |
| consumerServices | Payload industry as consumer services. |
| education | Payload industry as education. |
| energy | Payload industry as energy. |
| construction | Payload industry as construction. |
| consulting | Payload industry as consulting. |
| financialServices | Payload industry as financial services. |
| government | Payload industry as government. |
| hospitality | Payload industry as hospitality. |
| insurance | Payload industry as insurance. |
| legal | Payload industry as legal. |
| courierServices | Payload industry as courier services. |
| IT | Payload industry as IT. |
| healthcare | Payload industry as healthcare. |
| manufacturing | Payload industry as manufacturing. |
| retail | Payload industry as retail. |
| telecom | Payload industry as telecom. |
| realEstate | Payload industry as real estate. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

### payloadComplexity values

| Member | Description |
| :--- | :--- |
| unknown | The payload complexity is not defined. |
| low | The payload complexity is low. |
| medium | The payload complexity is medium. |
| high | The payload complexity is high. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.payload",
    "brand": "String",
    "complexity": "String",
    "createdBy": {"@odata.type": "microsoft.graph.emailIdentity"},
    "createdDateTime": "String (timestamp)",
    "description": "String",
    "detail": {"@odata.type": "microsoft.graph.payloadDetail"},
    "displayName": "String",
    "id": "String (identifier)",
    "industry": "String",
    "isAutomated": "Boolean",
    "isControversial": "Boolean",
    "isCurrentEvent": "Boolean",
    "language": "String",
    "lastModifiedBy": {"@odata.type": "microsoft.graph.emailIdentity"},
    "lastModifiedDateTime": "String (timestamp)",
    "payloadTags": ["String"],
    "platform": "String",
    "predictedCompromiseRate": "Double",
    "simulationAttackType": "String",
    "source": "String",
    "status": "String",
    "technique": "String",
    "theme": "String"
}
```

## Related content

- [Simulate a phishing attack](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training?view=o365-worldwide&preserve-view=true)
- [Get started using attack simulation training](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations).
