<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-permissiongrantpreapprovalpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Assign a permissionGrantPreApprovalPolicy to a servicePrincipal

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Assign a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object to [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All and Policy.ReadWrite.PermissionGrant | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.All and Policy.ReadWrite.PermissionGrant | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
POST /servicePrincipals/{id}/permissionGrantPreApprovalPolicies/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON object that contains an **@odata.id** parameter with a reference to a single [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/servicePrincipals/37d4ba51-cc54-4762-9ff7-deb5c9438cc7/permissionGrantPreApprovalPolicies/$ref
Content-Type: application/json

{
    "@odata.id": "https://graph.microsoft.com/beta/policies/permissionGrantPreApprovalPolicies/71ba13dc-5947-4e59-bcc5-0ad5c339a853"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permissionGrantPreApprovalPolicy = {
    '@odata.id': 'https://graph.microsoft.com/beta/policies/permissionGrantPreApprovalPolicies/71ba13dc-5947-4e59-bcc5-0ad5c339a853'
};

await client.api('/servicePrincipals/37d4ba51-cc54-4762-9ff7-deb5c9438cc7/permissionGrantPreApprovalPolicies/$ref')
	.version('beta')
	.post(permissionGrantPreApprovalPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
