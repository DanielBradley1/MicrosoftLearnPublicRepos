<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-post-forwardingprofiles?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Assign forwardingProfile

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Assign a forwarding profile to an existing remote network. To create a remote network with traffic forwarding profile, see [Create remoteNetwork](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-post-remotenetworks?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
PATCH /networkAccess/connectivity/remoteNetworks/{remoteNetworkId}/forwardingProfiles
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) object.

You can specify the following properties when associating a **forwardingProfile** to a remote network.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the forwarding profile. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). Required. |

## Response

If successful, this method returns a `OK 200` response code.

## Examples

To get the id of forwarding profiles of your organization, refer to this article - [List forwardingProfiles](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingprofiles?view=graph-rest-beta).

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks/{remoteNetworkId}/forwardingProfiles
Content-Type: application/json

{
    "@context": "#$delta",
    "value": [
        {
            "id": "1adaf535-1e31-4e14-983f-2270408162bf"
        }
    ]
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
```
