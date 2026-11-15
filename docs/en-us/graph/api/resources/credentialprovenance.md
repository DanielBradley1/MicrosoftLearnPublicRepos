<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/credentialprovenance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# credentialProvenance resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the provenance and trust classification configured in the **provenance** property of an [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-beta).

Credential provenance is recorded during credential registration and supports administrative attestation. The service computes the trust classification and records the actor that established the provenance.

To apply an administrative attestation, call the [attestProvenance](https://learn.microsoft.com/en-us/graph/api/authenticationmethod-attestprovenance?view=graph-rest-beta) action on the authentication method with an **attestationReason** and **verificationEventId**. The action supports delegated and application callers with the `CredentialProvenance.ReadWrite.All` permission and returns the updated **credentialProvenance** object. Classification, actor information, and timestamps are managed by the service.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assertedBy | [provenanceAssertedBy](https://learn.microsoft.com/en-us/graph/api/resources/provenanceassertedby?view=graph-rest-beta) | Identifies the actor that established the provenance. This property is computed by the service. |
| assertions | [provenanceAssertion](https://learn.microsoft.com/en-us/graph/api/resources/provenanceassertion?view=graph-rest-beta) collection | The assertions that support the credential's provenance classification. |
| chainStatus | [provenanceChainStatus](https://learn.microsoft.com/en-us/graph/api/resources/provenancechainstatus?view=graph-rest-beta) | The current integrity status of the credential's chain of trust. |
| classification | [provenanceClassification](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#provenanceclassification-values) | The service-computed trust classification. The possible values are: `highAssurance`, `mediumAssurance`, `lowAssurance`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.credentialProvenance",
  "assertedBy": {
    "@odata.type": "microsoft.graph.provenanceAssertedBy"
  },
  "assertions": [
    {
      "@odata.type": "microsoft.graph.provenanceAssertion"
    }
  ],
  "chainStatus": {
    "@odata.type": "microsoft.graph.provenanceChainStatus"
  },
  "classification": "String"
}
```
