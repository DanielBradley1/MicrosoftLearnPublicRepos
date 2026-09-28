<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-post-forwardingprofiles?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create forwardingProfile \(deprecated\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

Deprecated and to be retired soon. Use the [remoteNetwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) and its associated methods instead.

Create a new branch and assign a forwarding profile.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccessPolicy.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/connectivity/branches/{branchSiteId}/forwardingProfiles
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) object.

You can specify the following properties when creating a **forwardingProfile**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the branch. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). Required. |
| description | String | Description. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). Optional. |
| state | microsoft.graph.networkaccess.status | Status. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). The possible values are: `enabled`, `disabled`. Required. |
| associations | [microsoft.graph.networkaccess.association](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-association?view=graph-rest-beta) collection | The forwarding profile collection represents a group of multiple forwarding profiles. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/networkAccess/connectivity/branches/{branchSiteId}/
Content-Type: application/json

{
    "name": "branch 1",
    "region": "eastUS",
    "deviceLinks":
    [
        {
            "name": "device link 1",
            "ipAddress": "24.123.22.168",
            "deviceVendor": "intel",
            "bandwidthCapacityInMbps": "mbps250",
            "bgpConfiguration":
            {
                "localIpAddress": "1.128.24.22",
                "peerIpAddress": "1.128.24.28",
                "asn": 4,
            },
            "redundancyConfiguration":
            {
                "zoneLocalIpAddress": "1.128.23.20",
                "redundancyTier": "zoneRedundancy",
            },
            "tunnelConfiguration":
            {
                "@odata.type": "microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default",
                "preSharedKey": "/path/to/kv"
            }
        }
    ],
    "forwardingProfiles": [
        {
            "id": "8e30d8d6-3588-4d5f-a704-6bd843be5b8f"
        }
    ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const branchSite = {
    name: 'branch 1',
    region: 'eastUS',
    deviceLinks: 
    [
        {
            name: 'device link 1',
            ipAddress: '24.123.22.168',
            deviceVendor: 'intel',
            bandwidthCapacityInMbps: 'mbps250',
            bgpConfiguration: 
            {
                localIpAddress: '1.128.24.22',
                peerIpAddress: '1.128.24.28',
                asn: 4,
            },
            redundancyConfiguration: 
            {
                zoneLocalIpAddress: '1.128.23.20',
                redundancyTier: 'zoneRedundancy',
            },
            tunnelConfiguration: 
            {
                '@odata.type': 'microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default',
                preSharedKey: '/path/to/kv'
            }
        }
    ],
    forwardingProfiles: [
        {
            id: '8e30d8d6-3588-4d5f-a704-6bd843be5b8f'
        }
    ]
};

await client.api('/networkAccess/connectivity/branches/{branchSiteId}/')
	.version('beta')
	.post(branchSite);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://localhost:5001/networkaccess/connectivity/$metadata#branches/$entity",
    "id": "c038928c-4100-4b8d-895d-f90ae38bafa1",
    "name": "branch 1",
    "region": "eastUS",
    "connectivityState": "pending",
    "version": "1.0.0",
    "lastModifiedDateTime": "2021-01-05T00:00:00Z",
    "deviceLinks": [
        {
            "id": "f29753d5-85b4-4cce-9194-10a287568973",
            "name": "device link 1",
            "ipAddress": "24.123.22.168",
            "deviceVendor": "intel",
            "bandwidthCapacityInMbps": "mbps250",
            "bgpConfiguration":
            {
                "localIpAddress": "1.128.24.22",
                "peerIpAddress": "1.128.24.28",
                "asn": 4,
            },
            "redundancyConfiguration":
            {
                "zoneLocalIpAddress": "1.128.23.20",
                "redundancyTier": "zoneRedundancy",
            },
            "tunnleConfiguration": {
                "@odata.type": "#microsoft.graph.networkaccess.TunnleConfigurationIKEv2Deafult",
                "preSharedKey": "/path/to/kv"
            }
        }
    ],
    "forwardingProfiles": [
        {
            "id": "8e30d8d6-3588-4d5f-a704-6bd843be5b8f"
        }
    ]
}
```
