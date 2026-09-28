<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-29 -->

# Create agentIdentityBlueprintPrincipal object

Namespace: microsoft.graph

Create a new [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprintPrincipal.Create | AgentIdentityBlueprintPrincipal.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprintPrincipal.Create | AgentIdentityBlueprintPrincipal.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned one of the following roles:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)
  - [Agent ID Developer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-developer)

## HTTP request

```http
POST /servicePrincipals/microsoft.graph.agentIdentityBlueprintPrincipal
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object. The request body must contain **appId** of the [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object in the response body.

For information about errors returned by agent identity APIs, see [Agent identity error codes](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/error-codes).

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/microsoft.graph.agentIdentityBlueprintPrincipal
Content-type: application/json

{
  "appId": "00001111-aaaa-2222-bbbb-3333cccc4444"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentIdentityBlueprintPrincipal = {
  appId: '00001111-aaaa-2222-bbbb-3333cccc4444'
};

await client.api('/servicePrincipals/microsoft.graph.agentIdentityBlueprintPrincipal')
	.post(agentIdentityBlueprintPrincipal);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals/microsoft.graph.agentIdentityBlueprintPrincipal/$entity",
  "@odata.type": "#microsoft.graph.agentIdentityBlueprintPrincipal",
  "id": "59e617e5-e447-4adc-8b88-00af644d7c92",
  "accountEnabled": true,
  "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
  "appRoleAssignmentRequired": false,
  "createdByAppId": "00000003-0000-0000-c000-000000000000",
  "displayName": "foo",
  "publisherName": "Contoso",
  "servicePrincipalNames": [
      "00001111-aaaa-2222-bbbb-3333cccc4444"
  ],
  "signInAudience": "AzureADMyOrg",
  "servicePrincipalType": "Application",
  "tags": [],
  "appRoles": [],
  "info": {
      "termsOfServiceUrl": null,
      "supportUrl": null,
      "privacyStatementUrl": null,
      "marketingUrl": null,
      "logoUrl": null
  },
  "publishedPermissionScopes": []
}
```
