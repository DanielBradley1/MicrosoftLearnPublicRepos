<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# webApplicationFirewallVerificationResult resource type

Namespace: microsoft.graph

Represents the result of a [verification](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0) operation performed against a host or domain with a web application firewall \(WAF\) provider.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errors | [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0) collection | List of errors encountered during the verification process. |
| status | webApplicationFirewallVerificationStatus | Overall status of the verification operation. The possible values are: `success` \(verification passed\), `warning` \(verification completed with warnings\), `failure` \(verification failed\), `unknownFutureValue`. |
| verifiedOnDateTime | DateTimeOffset | UTC timestamp when the verification was performed or last updated. This indicates when the verification result was produced. |
| warnings | [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0) collection | List of warnings produced during verification. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webApplicationFirewallVerificationResult",
  "status": "String",
  "verifiedOnDateTime": "String (timestamp)",
  "errors": [
    {
      "@odata.type": "microsoft.graph.genericError"
    }
  ],
  "warnings": [
    {
      "@odata.type": "microsoft.graph.genericError"
    }
  ]
}
```
