<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provenanceassertion?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# provenanceAssertion resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an assertion that contributes to an authentication method's [credentialProvenance](https://learn.microsoft.com/en-us/graph/api/resources/credentialprovenance?view=graph-rest-beta) classification.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationReason | String | The reason supplied for a manual attestation. |
| eventDateTime | DateTimeOffset | The date and time of the provenance event represented by this assertion. |
| provenanceType | [provenanceAssertionType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#provenanceassertiontype-values) | The type of provenance assertion. The possible values are: `identityVerification`, `derivedFromCredential`, `manualAttestation`, `unknownFutureValue`. |
| sourceCredentialId | String | The identifier of the credential from which this credential was derived. |
| sourceCredentialType | String | The type of credential from which this credential was derived. |
| verificationEventId | String | The identifier of the [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) that supports this assertion. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.provenanceAssertion",
  "attestationReason": "String",
  "eventDateTime": "String (timestamp)",
  "provenanceType": "String",
  "sourceCredentialId": "String",
  "sourceCredentialType": "String",
  "verificationEventId": "String"
}
```
