<!-- Source: https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-list-applicationsegments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# List ipApplicationSegment objects

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.Read.All | Application.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.Read.All | Application.ReadWrite.All, Application.ReadWrite.OwnedBy |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

- *Application Administrator* and *Global Secure Access Administrator* are the least privileged roles supported for this operation.
- *Cloud Application Administrator* can't manage app proxy settings.

## HTTP request

```http
GET /applications/{applicationObjectId}/onPremisesPublishing/segmentsConfiguration/microsoft.graph.ipSegmentConfiguration/applicationSegments
```

## Optional query parameters

This method supports the `$expand` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/applications/dcc40202-6223-488b-8e64-28aa1a803d6c/onPremisesPublishing/segmentsConfiguration/microsoft.graph.IpSegmentConfiguration/ApplicationSegments
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applicationSegments = await client.api('/applications/dcc40202-6223-488b-8e64-28aa1a803d6c/onPremisesPublishing/segmentsConfiguration/microsoft.graph.IpSegmentConfiguration/ApplicationSegments')
	.version('beta')
	.get();
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
"value": [
        {
            "destinationHost": "test-check-ch.contoso.com",
            "destinationType": "fqdn",
            "port": 0,
            "ports": [
                "20-20"
            ],
            "protocol": "tcp",
            "id": "df8cb1a6-4bbf-4da3-8f85-fe2fc439ab80"
        },
        {
            "destinationHost": "5.6.7.8/28",
            "destinationType": "ipRangeCidr",
            "port": 0,
            "ports": [
                "25-25"
            ],
            "protocol": "tcp,udp",
            "id": "aab5b1be-40fd-43ef-92ae-1e86a696e686"
        },
        {
            "destinationHost": "test.contoso",
            "destinationType": "fqdn",
            "port": 0,
            "ports": [
                "20-20"
            ],
            "protocol": "tcp",
            "id": "55815c73-4c25-4b41-83c9-018dacf1edca"
        },
        {
            "destinationHost": "2.2.2.2/20",
            "destinationType": "ipRangeCidr",
            "port": 0,
            "ports": [
                "443-443"
            ],
            "protocol": "tcp",
            "id": "4f9ebb7f-545b-4b26-9c10-e47827e2421b"
        },
        {
            "destinationHost": "10.10.10.10",
            "destinationType": "ip",
            "port": 0,
            "ports": [
                "9-9"
            ],
            "protocol": "tcp,udp",
            "id": "95c92024-04e1-4569-bf9f-c2007afb04ba"
        },
        {
            "destinationHost": "check.contoso.com",
            "destinationType": "fqdn",
            "port": 0,
            "ports": [
                "443-443"
            ],
            "protocol": "tcp",
            "id": "f2b146fc-0a49-405b-9154-ad02b6b569fd"
        },
        {
            "destinationHost": "test",
            "destinationType": "fqdn",
            "port": 0,
            "ports": [
                "20-20"
            ],
            "protocol": "tcp",
            "id": "ce5ea5b9-c4f1-4734-9dae-8ee48c5b3de7"
        }
    ]
}
```
