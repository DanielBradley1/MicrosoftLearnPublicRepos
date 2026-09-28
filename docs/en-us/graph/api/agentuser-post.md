<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentuser-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create agentUser

Namespace: microsoft.graph

Create a new [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) object. You can also create an agent user by using the [POST /users](https://learn.microsoft.com/en-us/graph/api/user-post-users?view=graph-rest-1.0) endpoint and specifying the `microsoft.graph.agentUser` type in the request body.

At a minimum, you must specify the required properties. You can optionally specify any other writable properties.

This operation returns by default only a subset of the properties for each **agentUser**. These default properties are noted in the [Properties](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0#properties) section. To get properties that are not returned by default, do a [GET operation](https://learn.microsoft.com/en-us/graph/api/agentuser-get?view=graph-rest-1.0) and specify the properties in a `$select` OData query option.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdUser.ReadWrite.IdentityParentedBy | AgentIdUser.ReadWrite.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdUser.ReadWrite.IdentityParentedBy | AgentIdUser.ReadWrite.All, User.ReadWrite.All |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Agent ID Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /users/microsoft.graph.agentUser
```

Tip

You can also create agent users through the [POST /users](https://learn.microsoft.com/en-us/graph/api/user-post-users?view=graph-rest-1.0) without specifying the `microsoft.graph.agentUser` type. However, `"@odata.type": "microsoft.graph.agentUser"` must be specified in the request body together with other required properties for user creation.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) object.

The following table lists the properties that are *required* when you create an **agentUser**.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | `true` if the account is enabled; otherwise, `false`. |
| displayName | String | The name to display in the address book for the agent user. |
| mailNickname | String | The mail alias for the agent user. |
| userPrincipalName | String | The user principal name \(someagent@contoso.com\). It's an Internet-style login name for the agent user based on the Internet standard RFC 822. By convention, this should map to the agent user's email name. The general format is alias@domain, where domain must be present in the tenant's collection of verified domains. The verified domains for the tenant can be accessed from the **verifiedDomains** property of [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0).  <br>NOTE: This property cannot contain accent characters. Only the following characters are allowed `A - Z`, `a - z`, `0 - 9`, ` ' . - _ ! # ^ ~`. For the complete list of allowed characters, see [username policies](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-policy#userprincipalname-policies-that-apply-to-all-user-accounts). |
| identityParentId | String | The object ID of the associated [agent identity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0). Required. |

Because this resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), you can use the `POST` operation and add custom properties with your own data to the agent user instance while creating it.

## Response

If successful, this method returns a `201 Created` response code and an [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) object in the response body.

Attempting to create an agentUser with an **identityParentId** already linked to another agentUser returns a `400 Bad Request` error.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/users/microsoft.graph.agentUser
Content-type: application/json

{
  "accountEnabled": true,
  "displayName": "Sales Agent",
  "mailNickname": "SalesAgent",
  "userPrincipalName": "salesagent@contoso.com",
  "identityParentId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentUser = {
  accountEnabled: true,
  displayName: 'Sales Agent',
  mailNickname: 'SalesAgent',
  userPrincipalName: 'salesagent@contoso.com',
  identityParentId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890'
};

await client.api('/users/microsoft.graph.agentUser')
	.post(agentUser);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "@odata.type": "#microsoft.graph.agentUser",
    "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
    "businessPhones": [],
    "displayName": "Sales Agent",
    "mail": "salesagent@contoso.com",
    "mailNickname": "SalesAgent",
    "userPrincipalName": "salesagent@contoso.com",
    "identityParentId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
