<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantrelationship-put-multitenantorganization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create multiTenantOrganization

Namespace: microsoft.graph

Create a new multitenant organization. By default, the creator tenant becomes an owner tenant upon successful creation. Only owner tenants can manage a multitenant organization.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MultiTenantOrganization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MultiTenantOrganization.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PUT /tenantRelationships/multiTenantOrganization
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [multiTenantOrganization](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization?view=graph-rest-1.0) object.

You can specify the following properties when creating a **multiTenantOrganization**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the multitenant organization. Required. |
| description | String | Description of the multitenant organization. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [multiTenantOrganization](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization?view=graph-rest-1.0) object in the response body.

## Examples

The following example creates a new multitenant organization.

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization
Content-Type: application/json

{
  "displayName": "Contoso organization",
  "description": "Multitenant organization between Contoso, Fabrikam, and Woodgrove Bank"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const multiTenantOrganization = {
  displayName: 'Contoso organization',
  description: 'Multitenant organization between Contoso, Fabrikam, and Woodgrove Bank'
};

await client.api('/tenantRelationships/multiTenantOrganization')
	.put(multiTenantOrganization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/$entity",
    "id": "6d8b39e5-039a-4034-bf3a-e0b4f8cd60b6",
    "createdDateTime": "2023-05-26T22:05:23Z",
    "displayName": "Contoso organization",
    "description": "Multitenant organization between Contoso, Fabrikam, and Woodgrove Bank",
    "state": "active"
}
```
