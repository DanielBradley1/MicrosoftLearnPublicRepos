<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-post-devicelinks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create deviceLink

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create device link for a remote network. To create a remote network and device link in the same request, refer to [Create remote network](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-post-remotenetworks?view=graph-rest-beta).

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
POST /networkAccess/connectivity/remoteNetworks/{remoteNetworkId}/deviceLinks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object.

You can specify the following properties when creating a **deviceLink**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name or identifier associated with a device link. Required. |
| ipAddress | String | The IP address associated with a device link. Required. |
| deviceVendor | microsoft.graph.networkaccess.deviceVendor | The vendor or manufacturer of the device associated with a device link. The possible values are: `barracudaNetworks`, `checkPoint`, `ciscoMeraki`, `citrix`, `fortinet`, `hpeAruba`, `netFoundry`, `nuage`, `openSystems`, `paloAltoNetworks`, `riverbedTechnology`, `silverPeak`, `vmWareSdWan`, `versa`, `other`. Required. |
| tunnelConfiguration | [microsoft.graph.networkaccess.tunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfiguration?view=graph-rest-beta) | The tunnel configuration settings associated with a device link. Required. |
| bgpConfiguration | [microsoft.graph.networkaccess.bgpConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-bgpconfiguration?view=graph-rest-beta) | The Border Gateway Protocol \(BGP\) configuration settings associated with a device link. Required. |
| redundancyConfiguration | [microsoft.graph.networkaccess.redundancyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-redundancyconfiguration?view=graph-rest-beta) | The redundancy option for a device link specifies the specific details and configuration settings related to redundancy. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object in the response body.

## Example 1: Add a device link with default IKE policy

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks/dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04/deviceLinks
Content-Type: application/json
{
    "name": "CPE3",
    "ipAddress": "20.55.91.42",
    "deviceVendor": "ciscoMeraki",
    "bandwidthCapacityInMbps": "mbps1000",
    "bgpConfiguration": {
        "localIpAddress": "192.168.1.2",
        "peerIpAddress": "10.2.2.2",
        "asn": 65533
    },
    "redundancyConfiguration": {
        "redundancyTier": "zoneRedundancy",
        "zoneLocalIpAddress": "192.168.1.3"
    },
    "tunnelConfiguration": {
        "@odata.type": "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default",
        "preSharedKey": "test123"
    }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```

## Example 2: Add a device link with custom IKE policy

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks/dc6a7efd-6b2b-4c6a-84e7-5dcf97e62e04/deviceLinks
Content-Type: application/json

{
    "name": "custom link",
    "ipAddress": "114.20.4.14",
    "deviceVendor": "ciscoMeraki",
    "tunnelConfiguration": {
        "saLifeTimeSeconds": 300,
        "ipSecEncryption": "gcmAes128",
        "ipSecIntegrity": "gcmAes128",
        "ikeEncryption": "aes128",
        "ikeIntegrity": "sha256",
        "dhGroup": "ecp384",
        "pfsGroup": "ecp384",
        "@odata.type": "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Custom",
        "preSharedKey": "SHAREDKEY"
    },
    "bgpConfiguration": {
        "localIpAddress": "10.1.1.11",
        "peerIpAddress": "10.6.6.6",
        "asn": 65000
    },
    "redundancyConfiguration": {
        "redundancyTier": "zoneRedundancy",
        "zoneLocalIpAddress": "10.1.1.12"
    },
    "bandwidthCapacityInMbps": "mbps250"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{}
```
