<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-removekey?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# agentIdentityBlueprint: removeKey

Namespace: microsoft.graph

Remove a key credential from an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0). This method along with [addKey](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-addkey?view=graph-rest-1.0) can be used to automate rolling its expiring keys.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.AddRemoveCreds.All | AgentIdentityBlueprint.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.AddRemoveCreds.All | AgentIdentityBlueprint.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
POST /applications/{id}/microsoft.graph.agentIdentityBlueprint/removeKey
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide the following required properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| keyId | Guid | The unique identifier for the key. |
| proof | String | A self-signed JWT token used as a proof of possession of the existing keys. This JWT token must be signed using the private key of one of the application's existing valid certificates. The token should contain the following claims:<br><br>- **aud**: Audience needs to be `00000002-0000-0000-c000-000000000000`.<br>- **iss**: Issuer needs to be the ID of the **application** that initiates the request.<br>- **nbf**: Not before time.<br>- **exp**: Expiration time should be the value of **nbf** + 10 minutes.<br><br>  <br>For steps to generate this proof of possession token, see [Generating proof of possession tokens for rolling keys](https://learn.microsoft.com/en-us/graph/application-rollkey-prooftoken). |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/applications/{id}/microsoft.graph.agentIdentityBlueprint/removeKey
Content-Type: application/json

{
  "keyId": "Guid",
  "proof": "String"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const removeKey = {
  keyId: 'Guid',
  proof: 'String'
};

await client.api('/applications/{id}/microsoft.graph.agentIdentityBlueprint/removeKey')
	.post(removeKey);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
