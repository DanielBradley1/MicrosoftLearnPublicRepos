<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartreturnclaim?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# onTokenIssuanceStartReturnClaim resource type

Namespace: microsoft.graph

A claim returned by an API that is to be added to a token after the event when a token is about to be issued to your application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| claimIdInApiResponse | String | The identifier of the claim returned by an API that is to be add to a token being issued. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onTokenIssuanceStartReturnClaim",
  "claimIdInApiResponse": "String"
}
```
