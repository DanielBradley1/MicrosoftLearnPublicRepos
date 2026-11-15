<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provenancechainstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# provenanceChainStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the integrity status of the chain of trust for a [credentialProvenance](https://learn.microsoft.com/en-us/graph/api/resources/credentialprovenance?view=graph-rest-beta) object.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| breakDetectedAtDateTime | DateTimeOffset | The date and time when the service detected that the chain of trust was broken. |
| breakReason | [chainBreakReason](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#chainbreakreason-values) | The reason the chain of trust was broken. The possible values are: `none`, `idvRevoked`, `sourceCredentialRevoked`, `unknownFutureValue`. |
| breakSource | [chainBreakSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#chainbreaksource-values) | The source that detected or initiated the chain break. The possible values are: `none`, `identityProtection`, `adminAction`, `system`, `unknownFutureValue`. |
| state | [chainState](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#chainstate-values) | The current state of the chain of trust. The possible values are: `intact`, `broken`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.provenanceChainStatus",
  "breakDetectedAtDateTime": "String (timestamp)",
  "breakReason": "String",
  "breakSource": "String",
  "state": "String"
}
```
