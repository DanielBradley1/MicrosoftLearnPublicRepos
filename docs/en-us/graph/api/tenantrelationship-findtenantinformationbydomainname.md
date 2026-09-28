<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantrelationship-findtenantinformationbydomainname?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-06 -->

# tenantRelationship: findTenantInformationByDomainName

Namespace: microsoft.graph

Given a domain name, search for a tenant and read its [tenantInformation](https://learn.microsoft.com/en-us/graph/api/resources/tenantinformation?view=graph-rest-1.0). You can use this API to validate tenant information and use the **tenantId** to [configure cross-tenant access settings between you and the tenant](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CrossTenantInformation.ReadBasic.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CrossTenantInformation.ReadBasic.All | Not available. |

Important

This API operation doesn't require the calling user to be assigned any [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json).

## HTTP request

```http
GET /tenantRelationships/findTenantInformationByDomainName(domainName='{id}')
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table shows the parameters that must be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| domainName | String | Primary domain name of a Microsoft Entra tenant. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [tenantInformation](https://learn.microsoft.com/en-us/graph/api/resources/tenantinformation?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/v1.0/tenantRelationships/findTenantInformationByDomainName(domainName='contoso.com')
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let tenantInformation = await client.api('/tenantRelationships/findTenantInformationByDomainName(domainName='contoso.com')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.tenantInformation",
    "tenantId": "6babcaad-604b-40ac-a9d7-9fd97c0b779f",
    "federationBrandName": null,
    "displayName": "Contoso, Ltd",
    "defaultDomainName": "contoso.com"
}
```
