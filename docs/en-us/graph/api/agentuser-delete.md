<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentuser-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Delete agentUser

Namespace: microsoft.graph

Delete an [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdUser.ReadWrite.IdentityParentedBy | AgentIdUser.ReadWrite.All, User.DeleteRestore.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdUser.ReadWrite.IdentityParentedBy | AgentIdUser.ReadWrite.All, User.DeleteRestore.All, User.ReadWrite.All |

Important

The calling user must be assigned at least one of the following [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json):

- User Administrator
- Privileged Authentication Administrator
- Agent ID Administrator

To delete users with privileged administrator roles in delegated scenarios, the app must be assigned the *Directory.AccessAsUser.All* delegated permission, and the calling user must have a higher privileged administrator role as indicated in [Who can perform sensitive actions](https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions).

In app-only scenarios, the *User.ReadWrite.All* application permission isn't enough privilege to delete users with privileged administrative roles. The agent must be assigned a higher privileged administrator role as indicated in [Who can perform sensitive actions](https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions).

## HTTP request

```http
DELETE /users/microsoft.graph.agentUser/{userId}
```

Note: An agent user can be deleted through the standard users' endpoint as well: DELETE /users/userId. No special odata type needs to be specified in the request.

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

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
DELETE https://graph.microsoft.com/v1.0/users/microsoft.graph.agentUser/ba9a3254-9f18-4209-aeb3-9e42a35b5be4 
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/microsoft.graph.agentUser/ba9a3254-9f18-4209-aeb3-9e42a35b5be4')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
