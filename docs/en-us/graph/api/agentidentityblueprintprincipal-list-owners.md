<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-list-owners?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List agentIdentityBlueprintPrincipal owners

Namespace: microsoft.graph

Retrieve a list of owners of the [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprintPrincipal.Read.All | Application.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprintPrincipal.Read.All | Application.Read.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
GET /servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal/owners
```

## Optional query parameters

This method supports the `$select` and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/serviceprincipals/bbec3106-565f-4907-941e-96b4dbfef21c/microsoft.graph.agentIdentityBlueprintPrincipal/owners
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let owners = await client.api('/serviceprincipals/bbec3106-565f-4907-941e-96b4dbfef21c/microsoft.graph.agentIdentityBlueprintPrincipal/owners')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryObjects",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET servicePrincipals(appId=<key>)/owners?$select=deletedDateTime",
    "value": [
        {
            "@odata.type": "#microsoft.graph.user",
            "id": "ce4770b3-70b2-4a38-a242-76631e9f7408",
            "accountEnabled": null,
            "city": null,
            "createdDateTime": null,
            "displayName": null,
            "mail": null,
            "mailNickname": null,
            "otherMails": [],
            "proxyAddresses": [],
            "surname": null,
            "userPrincipalName": null,
            "userType": null
        },
        {
            "@odata.type": "#microsoft.graph.user",
            "id": "858a9c90-38b3-4e78-b915-234aece712c4"
        },
        {
            "@odata.type": "#microsoft.graph.user",
            "id": "7585d967-f300-43de-b817-7119a6404c5e"
        }
    ]
}
```
