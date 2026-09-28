<!-- Source: https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Delete synchronizationSchema

Namespace: microsoft.graph

Delete the customized [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0) and resets the schema to the default configuration. If the schema is deleted in the context of the template, it resets the schema to the default one associated with the template's `factoryTag`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Synchronization.ReadWrite.All | CustomSecAttributeProvisioning.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | CustomSecAttributeProvisioning.ReadWrite.All, Synchronization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator
- Hybrid Identity Administrator - to configure Microsoft Entra Cloud Sync

## HTTP Request

```http
DELETE /servicePrincipals/{id}/synchronization/jobs/{jobId}/schema
DELETE /applications/{id}/synchronization/templates/{templateId}/schema
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `201 No Content` response code. It doesn't return anything in response body.

## Example

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/servicePrincipals/{id}/synchronization/jobs/{jobId}/schema
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
