<!-- Source: https://learn.microsoft.com/en-us/graph/api/impactedresource-removetag?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# impactedResource: removeTag

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Remove a user-defined [tag](https://learn.microsoft.com/en-us/graph/api/resources/recommendationtag?view=graph-rest-beta) from an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object. To remove the same tag from multiple impacted resources in a single request, use the [removeTag](https://learn.microsoft.com/en-us/graph/api/impactedresource-removetag-collection?view=graph-rest-beta) action on the impactedResources collection.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DirectoryRecommendations.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DirectoryRecommendations.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Administrator
- Security Operator
- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
POST /directory/recommendations/{recommendationId}/impactedResources/{impactedResourceId}/removeTag
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| tagId | String | The unique identifier of the [recommendationTag](https://learn.microsoft.com/en-us/graph/api/resources/recommendationtag?view=graph-rest-beta) to remove from the impacted resource. Required. |

## Response

If successful, this action returns a `200 OK` response code and an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/directory/recommendations/0cb31920-84b9-471f-a6fb-468c1a847088_Microsoft.Identity.IAM.Insights.ApplicationCredentialExpiry/impactedResources/dbd9935e-15b7-4800-9049-8d8704c23ad2/removeTag
Content-Type: application/json

{
    "tagId": "6f9a1e17-8e2f-4a2c-9f3b-1d0e5c7a2b34"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#impactedResource",
  "@odata.type": "#microsoft.graph.impactedResource",
  "id": "dbd9935e-15b7-4800-9049-8d8704c23ad2",
  "recommendationId": "0cb31920-84b9-471f-a6fb-468c1a847088_Microsoft.Identity.IAM.Insights.ApplicationCredentialExpiry",
  "displayName": "Contoso IWA App Tutorial"
}
```
