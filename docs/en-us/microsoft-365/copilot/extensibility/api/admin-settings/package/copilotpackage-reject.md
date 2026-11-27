<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-reject -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackage: reject

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Reject a pending Copilot package title submission. This action reviews a package title and its submitted version; it doesn't reject an individual user's request. Use the title ID confirmed for reviewing the pending submission, not the `identifier` of a [copilotPackageRequestInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestinfo) object. The ID used to retrieve package details isn't necessarily interchangeable with the ID accepted for title review.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotPackages.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotPackages.ReadWrite.All | Not available. |

## HTTP request

```http
POST https://graph.microsoft.com/beta/copilot/admin/catalog/packages/{packageId}/reject
```

Replace `{packageId}` with the title ID confirmed for reviewing the pending submission. Don't substitute an individual request identifier.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. For more information, see [Authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required when supplying a request body. |

## Request body

The schema defines both parameters as optional. This doesn't mean that omitting `version` selects the latest or pending version. Supply the version of the staged submission you're rejecting.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `reviewerComment` | String | Optional explanation for the rejection. |
| `version` | String | Version of the staged package title submission to reject. Optional in the schema; use the matching submitted version to target a specific review. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

This example assumes that the package owner has confirmed `{packageId}` as the title ID for reviewing the pending submission and that its submitted version is `1.2.3`. Replace the placeholder with that confirmed ID. Don't infer it from a package-detail path or response ID, and don't use an individual request's identifier.

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/copilot/admin/catalog/packages/{packageId}/reject
Content-Type: application/json

{
  "version": "1.2.3",
  "reviewerComment": "The submitted title needs revision."
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
