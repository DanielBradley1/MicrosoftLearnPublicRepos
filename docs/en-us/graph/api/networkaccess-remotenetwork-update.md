<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update remoteNetwork

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the configuration or properties of a specific remote network.

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
PATCH /networkAccess/connectivity/remoteNetworks/{remoteNetworkId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the remote network. |

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following is an example of a request.

```http
PATCH https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks/dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04
Content-Type: application/json

{
    "name": "Test Redmond branch"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks/$entity",
    "id": "dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04",
    "name": "Test Redmond branch",
    "region": "canadaEast",
    "version": "1.0.0",
    "lastModifiedDateTime": "2024-01-27T06:16:14Z",
    "forwardingProfiles@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks('dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04')/forwardingProfiles",
    "forwardingProfiles": [],
    "deviceLinks@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks('dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04')/deviceLinks",
    "deviceLinks": [
        {
            "id": "47aab2e9-7f5c-42ba-bbfc-1b049193126a",
            "name": "name",
            "ipAddress": "1.2.3.1",
            "bandwidthCapacityInMbps": "mbps500",
            "deviceVendor": "barracudaNetworks",
            "lastModifiedDateTime": "2024-01-27T06:16:14Z",
            "bgpConfiguration": {
                "localIpAddress": "1.2.1.1",
                "peerIpAddress": "1.2.3.1",
                "asn": 899
            },
            "redundancyConfiguration": {
                "zoneLocalIpAddress": null,
                "redundancyTier": "noRedundancy"
            },
            "tunnelConfiguration": {
                "@odata.type": "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default",
                "preSharedKey": "dcf"
            }
        }
    ]
}
```
