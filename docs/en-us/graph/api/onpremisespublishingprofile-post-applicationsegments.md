<!-- Source: https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-post-applicationsegments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create ipApplicationSegment

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.All | Application.ReadWrite.OwnedBy |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

- *Application Administrator* is the least privileged role supported for this operation.
- *Cloud Application Administrator* can't manage app proxy settings.

## HTTP request

```http
POST /applications/{applicationObjectId}/onPremisesPublishing/segmentsConfiguration/microsoft.graph.ipSegmentConfiguration/applicationSegments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) object.

You can specify the following properties when creating an **ipApplicationSegment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| destinationHost | String | Either the IP address, IP range, or FQDN of the **applicationSegment**, with or without wildcards. |
| destinationType | privateNetworkDestinationType | The possible values are: `ipAddress`, `ipRange`, `ipRangeCidr`, `fqdn`, `dnsSuffix`. |
| ports | String collection | List of ports supported for the application segment. |
| protocol | privateNetworkProtocol | Indicates the protocol of the network traffic acquired for the application segment. The possible values are: `tcp`, `udp`. |

## Response

If successful, this method returns a `201 Created` response code and an [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/applications/dcc40202-6223-488b-8e64-28aa1a803d6c/onPremisesPublishing/segmentsConfiguration/microsoft.graph.IpSegmentConfiguration/ApplicationSegments
Content-Type: application/json

{
   "destinationHost": "test2.com",
   "destinationType": "fqdn",
   "port": 0,
   "ports": [
      "445-445",
      "3389-3389"
   ],
   "protocol": "tcp"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ipApplicationSegment = {
   destinationHost: 'test2.com',
   destinationType: 'fqdn',
   port: 0,
   ports: [
      '445-445',
      '3389-3389'
   ],
   protocol: 'tcp'
};

await client.api('/applications/dcc40202-6223-488b-8e64-28aa1a803d6c/onPremisesPublishing/segmentsConfiguration/microsoft.graph.IpSegmentConfiguration/ApplicationSegments')
	.version('beta')
	.post(ipApplicationSegment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#applications('8706aca4-94e9-4783-a23d-7dae1599a6e0')/onPremisesPublishing/segmentsConfiguration/microsoft.graph.ipSegmentConfiguration/applicationSegments/$entity",
    "destinationHost": "test2.com",
    "destinationType": "fqdn",
    "port": 0,
    "ports": [
        "445-445",
        "3389-3389"
    ],
    "protocol": "tcp",
    "id": "2b52958c-9d0c-449d-a985-c29d488a6335"
}
```
