<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# List forwardingPolicies

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve a list of forwarding policies associated with a specific traffic forwarding profile.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.Read.All | NetworkAccess.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.Read.All | NetworkAccess.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/forwardingPolicies
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

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.networkaccess.forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/{forwardingProfileId}/forwardingPolicies
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/forwardingProfiles('a5bb6d50-dbe3-4767-b883-12e1a915bc53')/policies",
    "value": [
        {
            "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicyLink",
            "id": "3ef2446f-7ddf-4e80-af04-821534489155",
            "state": "enabled",
            "version": "1.0.0",
            "policy": {
                "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicy",
                "id": "81e6666b-dcf3-4ee6-9212-adb12df18dab",
                "name": "Exchange Online",
                "description": "These properties represent Exchange Online endpoints that should be reachable to use the service.",
                "version": "1.0.0",
                "trafficForwardingType": "m365"
            }
        },
        {
            "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicyLink",
            "id": "c0eea492-85f4-4eab-b03a-3a5abb459096",
            "state": "enabled",
            "version": "1.0.0",
            "policy": {
                "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicy",
                "id": "d8929d18-b24a-4a67-8c7b-1483029855a0",
                "name": "SharePoint Online and OneDrive for Business",
                "description": "These properties represent SharePoint Online and OneDrive for Business endpoints that should be reachable to use the service.",
                "version": "1.0.0",
                "trafficForwardingType": "m365"
            }
        },
        {
            "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicyLink",
            "id": "caaa9df8-240c-4db1-ad34-0c9b5ca06918",
            "state": "enabled",
            "version": "1.0.0",
            "policy": {
                "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicy",
                "id": "c67e7847-feab-4b13-8163-88c0bac70ad0",
                "name": "Microsoft 365 Common and Office Online",
                "description": "These properties represent Microsoft 365 Common and Office Online endpoints that should be reachable to use the service.",
                "version": "1.0.0",
                "trafficForwardingType": "m365"
            }
        }
    ]
}
```
