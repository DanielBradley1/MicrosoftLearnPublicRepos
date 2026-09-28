<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmissionpolicy-delete?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Delete emailThreatSubmissionPolicy

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete an [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ThreatSubmissionPolicies.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ThreatSubmissionPolicy.ReadWrite.All | Not available. |

## HTTP request

```http
DELETE /security/threatSubmission/emailThreatSubmissionPolicies/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

```http
DELETE https://graph.microsoft.com/beta/security/threatSubmission/emailThreatSubmissionPolices/{id}
```

### Response

```http
HTTP/1.1 204 No Content
```
