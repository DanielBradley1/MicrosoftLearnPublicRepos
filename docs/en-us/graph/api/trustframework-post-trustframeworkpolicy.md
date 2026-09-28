<!-- Source: https://learn.microsoft.com/en-us/graph/api/trustframework-post-trustframeworkpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-27 -->

# Create trustFrameworkPolicy

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

Create new [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.TrustFramework | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.TrustFramework | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *B2C IEF Policy Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /trustFramework/policies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/xml. Required. |

## Request body

In the request body, provide an XML representation of the [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta) object. The content type must be `application/xml`.

## Response

If successful, this method returns a `201 Created` response code and [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta) object in the response body. If unsuccessful, a `4xx` error will be returned with specific details.

## Example

The following example creates a **trustFrameworkPolicy**.

### Request

```http
POST https://graph.microsoft.com/beta/trustFramework/policies
Content-Type: application/xml

<TrustFrameworkPolicy xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/online/cpim/schemas/2013/06" PolicySchemaVersion="0.3.0.0" TenantId="contoso.com" PolicyId="B2C_1A_SocialAndLocalAccounts_Base">
    <!---PolicyContent-->
</TrustFrameworkPolicy>
```

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/xml
Location: /trustFramework/policies/B2C_1A_SocialAndLocalAccounts_Base/

<TrustFrameworkPolicy xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/online/cpim/schemas/2013/06" PolicySchemaVersion="0.3.0.0" TenantId="contoso.com" PolicyId="B2C_1A_SocialAndLocalAccounts_Base" PublicPolicyUri="http://contoso.com/B2C_1A_Test">
    <!---PolicyContent-->
</TrustFrameworkPolicy>
```
