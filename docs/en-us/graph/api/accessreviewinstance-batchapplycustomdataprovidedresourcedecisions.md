<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-batchapplycustomdataprovidedresourcedecisions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# accessReviewInstance: batchApplyCustomDataProvidedResourceDecisions

Namespace: microsoft.graph

Enables reviewers to set the **applyResult** and **applyDescription** on all [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) objects in a specific [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) in batches by using **customDataProvidedResourceId**.

**NOTE:** The access review instance must be in an `Applying` state.

This action is part of the unified access reviews surface and is available only through the `/identityGovernance/accessReviews/unified` route. For more information, see [unifiedRoot](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroot?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AccessReview.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AccessReview.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- To write access reviews of a group or app: *User Administrator*, *Identity Governance Administrator*
- To write access reviews of a Microsoft Entra role: *Identity Governance Administrator*, *Privileged Role Administrator*

## HTTP request

```http
POST /identityGovernance/accessReviews/unified/instances/{accessReviewInstanceId}/batchApplyCustomDataProvidedResourceDecisions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| applyResult | [accessReviewInstanceDecisionItemApplyResult](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#accessreviewinstancedecisionitemapplyresult-values) | The `applyResult` for the entity being reviewed. The possible values are: `new`, `appliedSuccessfully`, `appliedWithUnknownFailure`, `appliedSuccessfullyButObjectNotFound`, `applyNotSupported`, `unknownFutureValue`. Required. |
| applyDescription | String | If supplied, a description for the `applyResult`. Optional. |
| customDataProvidedResourceId | String | The `applyResult` is set on all **accessReviewInstanceDecisionItem** objects whose custom data provided resource `id` matches the supplied **customDataProvidedResourceId**. Required. |

## Response

If successful, this action returns a `202 Accepted` response code.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/unified/instances/{accessReviewInstanceId}/batchApplyCustomDataProvidedResourceDecisions
Content-Type: application/json

{
  "applyResult": "appliedSuccessfully",
  "applyDescription": "Access was removed from production application: GitHub-app.",
  "customDataProvidedResourceId": "5c728447-be5c-4565-b4d3-cb248b609891"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
