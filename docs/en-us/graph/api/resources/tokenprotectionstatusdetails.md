<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tokenprotectionstatusdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# tokenProtectionStatusDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The status of token protection for a request in the sign-in logs. `bound` requests pass a conditional access session control for token protection. More detail might be provided in the **signInSessionStatusCode** property. For more information, see [Conditional Access: Token Protection](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-token-protection). This object is configured in the **tokenProtectionStatusDetails** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| signInSessionStatus | tokenProtectionStatus | The token protection status of the sign-in session. The possible values are: `none`, `bound`, `unbound`, `unknownFutureValue`. |
| signInSessionStatusCode | Int32 | Additional information about the status. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tokenProtectionStatusDetails",
  "signInSessionStatus": "String",
  "signInSessionStatusCode": "Integer"
}
```
