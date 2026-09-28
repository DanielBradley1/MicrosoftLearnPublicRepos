<!-- Source: https://learn.microsoft.com/en-us/graph/api/trustframework-put-trustframeworkpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Update or create trustFrameworkPolicy

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

Update an existing [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta) or create one if it doesn't exist.

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
PUT /trustFramework/policies/{id}/$value
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/xml. Required. |

## Request body

In the request body, provide an XML representation of the [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta) object.

> **Note:** the content type must be `application/xml`.

## Response

The response will be one of the following:

- If a [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta) exists, a successful request returns a `200 OK` response code.
- If a [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta) doesn't exist, a successful request returns a `201 Created` response code.
- If unsuccessful, a `4xx` error will be returned with specific details.

## Example

The following example updates a **trustFrameworkPolicy**.

### Request

```http
PUT https://graph.microsoft.com/beta/trustFramework/policies/B2C_1A_SocialAndLocalAccounts_Base/$value
Content-Type: application/xml

<TrustFrameworkPolicy xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/online/cpim/schemas/2013/06" PolicySchemaVersion="0.3.0.0" TenantId="contoso.com" PolicyId="B2C_1A_SocialAndLocalAccounts_Base">
    <!---PolicyContent-->
</TrustFrameworkPolicy>
```

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/xml

<TrustFrameworkPolicy xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/online/cpim/schemas/2013/06" PolicySchemaVersion="0.3.0.0" TenantId="contoso.com" PolicyId="B2C_1A_Test" PublicPolicyUri="http://contoso.com/B2C_1A_Test">
    .....
    ....
    <!---PolicyContent-->
    ....
    ....
</TrustFrameworkPolicy>
```
