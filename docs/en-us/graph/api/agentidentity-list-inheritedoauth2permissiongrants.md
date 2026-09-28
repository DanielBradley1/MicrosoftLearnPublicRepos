<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentity-list-inheritedoauth2permissiongrants?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# List inherited OAuth2 permission grants for an agent identity

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the delegated permission grants \([oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-beta) objects\) that an [agent identity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-beta) inherits from its parent agent identity blueprint principal. These inherited grants represent the effective delegated permissions applied at token issuance time.

This endpoint returns only inherited grants where `consentType` is `AllPrincipals` \(admin-consented, tenant-wide grants\). Grants where `consentType` is `Principal` \(user-specific grants\) are not returned by this endpoint.

The inherited collection is strictly read-only. POST, PATCH, and DELETE requests return `405 Method Not Allowed`. To modify the permissions that agent identities inherit, update the parent agent identity blueprint principal's `oauth2PermissionGrants` instead.

Pagination is not supported. All results are returned in a single response. `$top`, `$skip`, and `$skiptoken` are not supported.

Calling this endpoint on a service principal that is not an agent identity returns `404 Not Found`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | DelegatedPermissionGrant.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | DelegatedPermissionGrant.ReadWrite.All, Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Readers
- Global Reader
- Application Developer
- Directory Writers
- Cloud Application Administrator
- Application Administrator
- Privileged Role Administrator
- User Administrator
- Directory Synchronization Accounts - for Microsoft Entra Connect and Microsoft Entra Cloud Sync services

## HTTP request

```http
GET /servicePrincipals/microsoft.graph.agentIdentity/{agentIdentity-id}/inheritedOauth2PermissionGrants
```

## Optional query parameters

This method doesn't support OData query parameters.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/servicePrincipals/microsoft.graph.agentIdentity/b3f37624-8113-471c-9de3-0234828e3ca2/inheritedOauth2PermissionGrants
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let inheritedOauth2PermissionGrants = await client.api('/servicePrincipals/microsoft.graph.agentIdentity/b3f37624-8113-471c-9de3-0234828e3ca2/inheritedOauth2PermissionGrants')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "abc123def456",
      "clientId": "b3f37624-8113-471c-9de3-0234828e3ca2",
      "consentType": "AllPrincipals",
      "principalId": null,
      "resourceId": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
      "scope": "User.Read Mail.Read",
      "startTime": "2026-06-15T00:00:00Z",
      "expiryTime": "2027-06-15T00:00:00Z"
    }
  ]
}
```
