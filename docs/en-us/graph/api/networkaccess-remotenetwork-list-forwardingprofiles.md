<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-list-forwardingprofiles?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# List forwardingProfiles \(for a remote network\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve a list of traffic forwarding profiles associated with a remote network.

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

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/connectivity/remoteNetworks/{remoteNetworkId}/forwardingProfiles
```

## Optional query parameters

This method doesn't support any OData query parameters.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following is an example of a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks/dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04/forwardingProfiles
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "http://graph.microsoft.com/beta/networkAccess/$metadata#forwardingProfiles",
    "value": [
        {
            "id": "19a92090-c14e-4cea-a933-27d38f72c4d1",
            "name": "forwardingProfile 1",
            "description": "some description",
            "state": "disabled",
            "version": "13",
            "lastModifiedDate": "2022-06-13T08:22:14Z",
            "trafficForwardingType": "m365",
            "priority": 500,
            "associations" : [
                {
                 "@odata.type": "microsoft.graph.networkAccess.AssociatedBranch",
                 "branchId": "19a92090-c14e-4cea-a933-27d38f72c64s"
                }                
            ],
        }       
    ]
}
```
