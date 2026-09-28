<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Get remoteNetwork

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve information about a specific remote network.

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
GET /networkAccess/connectivity/remoteNetworks/{remoteNetworkId}
```

## Optional query parameters

This method supports the `$expand` and `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.networkaccess.remoteNetworks](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks/dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET networkAccess/connectivity/remoteNetworks('<guid>')?$select=bandwidthCapacity,connectivityState",
    "id": "dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04",
    "name": "Test branch",
    "region": "canadaEast",
    "version": "1.0.0",
    "lastModifiedDateTime": "2023-12-12T14:26:24Z",
    "forwardingProfiles@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks('dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04')/forwardingProfiles",
    "forwardingProfiles": [
        {
            "trafficForwardingType": "m365",
            "priority": 0,
            "id": "1adaf535-1e31-4e14-983f-2270408162bf",
            "name": "Microsoft 365 traffic forwarding profile",
            "description": "Default traffic forwarding profile for Microsoft 365 traffic acquisition. Assign the profile to client or branch offices to acquire Microsoft 365 traffic for Zero Trust Network Access.",
            "state": "disabled",
            "version": "1.0.0",
            "lastModifiedDateTime": "2024-01-22T12:10:49Z",
            "associations": [
                {
                    "@odata.type": "#microsoft.graph.networkaccess.associatedBranch",
                    "branchId": "9ffbc1a5-2916-4fb4-b277-76cdc89cc491"
                },
                {
                    "@odata.type": "#microsoft.graph.networkaccess.associatedBranch",
                    "branchId": "dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04"
                },
                {
                    "@odata.type": "#microsoft.graph.networkaccess.associatedBranch",
                    "branchId": "43c7a0d3-1072-4da1-9e30-e513b02bb559"
                },
                {
                    "@odata.type": "#microsoft.graph.networkaccess.associatedBranch",
                    "branchId": "4ecfc62c-ec85-42fd-af37-5a93c7deb1d9"
                }
            ]
        }
    ],
    "deviceLinks@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks('dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04')/deviceLinks",
    "deviceLinks": [
        {
            "id": "47aab2e9-7f5c-42ba-bbfc-1b049193126a",
            "name": "name",
            "ipAddress": "1.2.3.1",
            "bandwidthCapacityInMbps": "mbps500",
            "deviceVendor": "barracudaNetworks",
            "lastModifiedDateTime": "2023-12-12T14:26:24Z",
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
