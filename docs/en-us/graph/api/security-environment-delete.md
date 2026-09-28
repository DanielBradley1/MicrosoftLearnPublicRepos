<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-environment-delete?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-10 -->

# Delete environment

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete an [environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) object from a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object by providing the environment ID. The environment ID should be URL-encoded.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Zone.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Zone.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
DELETE /security/zones/{zoneId}/environments/{environmentId}
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

The following example shows a request to detach an Azure subscription environment from a zone.

The environment ID for Azure subscriptions uses the `/subscriptions/{subscription-id}` format and must be URL-encoded when used in the request URL.

| Format | Value |
| :--- | :--- |
| Original | `/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15` |
| URL-encoded | `%2Fsubscriptions%2Fd34fd44c-ebfa-4a9c-bceb-9eeafe72ac15` |

```http
DELETE https://graph.microsoft.com/beta/security/zones/f6e190cba2f64bcba703694aedb81712/environments/%2Fsubscriptions%2Fd34fd44c-ebfa-4a9c-bceb-9eeafe72ac15
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
