<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetworkconnectivityconfiguration-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Get remoteNetworkConnectivityConfiguration

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the IPSec tunnel configuration required to establish a bidirectional communication link between your organization's router and the Microsoft gateway. This information is vital for configuring your router \(customer premise equipment\) after creating a [deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta). Refer to [Configure customer premises equipment for Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-customer-premises-equipment?tabs=microsoft-entra-admin-center) to understand how to use this information to set up your router.

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
GET /networkAccess/connectivity/remoteNetworks/{remoteNetworkId}/connectivityConfiguration
```

## Optional query parameters

This method doesn't supports OData query parameters.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.networkaccess.remoteNetworkConnectivityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkconnectivityconfiguration?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks/dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04/connectivityConfiguration
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks('4ecfc62c-ec85-42fd-af37-5a93c7deb1d9')/connectivityConfiguration/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET networkAccess/connectivity/remoteNetworks('<guid>')/connectivityConfiguration?$select=remoteNetworkId,remoteNetworkName",
    "remoteNetworkId": "4ecfc62c-ec85-42fd-af37-5a93c7deb1d9",
    "remoteNetworkName": "Abhijeet Azure VNG",
    "links@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks('4ecfc62c-ec85-42fd-af37-5a93c7deb1d9')/connectivityConfiguration/links",
    "links": [
        {
            "id": "109376bf-6dc7-4183-ab11-4a1206fb5e90",
            "displayName": "VNG",
            "localConfigurations": [
                {
                    "endpoint": "20.245.111.21",
                    "asn": 65476,
                    "bgpAddress": "192.168.1.2",
                    "region": "westUS"
                },
                {
                    "endpoint": "20.245.111.77",
                    "asn": 65476,
                    "bgpAddress": "192.168.1.3",
                    "region": "westUS"
                }
            ],
            "peerConfiguration": {
                "endpoint": "20.172.65.16",
                "asn": 65533,
                "bgpAddress": "10.0.2.5"
            }
        }
    ]
}
```
