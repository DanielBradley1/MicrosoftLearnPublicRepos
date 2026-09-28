<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/requestsignatureverification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# requestSignatureVerification resource type

Namespace: microsoft.graph

Specifies whether this application requires Microsoft Entra ID to verify the signed authentication requests.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedWeakAlgorithms | weakAlgorithms | Specifies which weak algorithms are allowed.  <br>  <br>The possible values are: `rsaSha1`, `unknownFutureValue`. |
| isSignedRequestRequired | Boolean | Specifies whether signed authentication requests for this application should be required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.requestSignatureVerification",
  "isSignedRequestRequired": "Boolean",
  "allowedWeakAlgorithms": "String"
}
```
