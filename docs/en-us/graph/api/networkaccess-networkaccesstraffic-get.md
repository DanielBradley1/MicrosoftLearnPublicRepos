<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccesstraffic-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-30 -->

# Get networkAccessTraffic

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the properties and relationships of a [networkAccessTraffic](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-networkaccesstraffic?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess-Reports.Read.All | NetworkAccess.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess-Reports.Read.All | NetworkAccess.ReadWrite.All |

## HTTP request

```http
GET /networkAccess/logs/traffic/{transactionId}
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [networkAccessTraffic](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-networkaccesstraffic?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following is an example of a request.

```msgraph
GET https://graph.microsoft.com/beta/networkAccess/logs/traffic/5062f456-9d9e-477b-b788-b7aa6b5d402b
```

### Response

The following is an example of the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/logs/traffic/$entity",
  "transactionId": "5062f456-9d9e-477b-b788-b7aa6b5d402b",
  "createdDateTime": "2025-04-02T15:30:45Z",
  "tenantId": "5c3b997a-7ef9-4b2a-a63b-0271df6ace3b",
  "connectionId": "6d3c2e8f-9a1b-4c7d-8e5f-0231df6ace1a",
  "sessionId": "7f2d1b9e-8c0a-5d6e-9f4e-1342ef7bdf2c",
  "trafficType": "internet",
  "deviceCategory": "client",
  "destinationIp": "203.0.113.5",
  "destinationPort": 443,
  "destinationFQDN": "example.com",
  "destinationUrl": "https://example.com/resources/document.pdf",
  "sourceIp": "192.168.1.100",
  "sourcePort": 54321,
  "deviceOperatingSystem": "Windows 11",
  "deviceOperatingSystemVersion": "22H2",
  "agentVersion": "1.0.123.45",
  "deviceId": "4c8b9a7d-6e5f-3c2d-1b0a-9f8e7d6c5b4a",
  "userId": "2a3b4c5d-6e7f-8g9h-0i1j-2k3l4m5n6o7p",
  "userPrincipalName": "user@contoso.com",
  "transportProtocol": "tcp",
  "networkProtocol": "tcp",
  "action": "allow",
  "policyRuleId": "3d4e5f6g-7h8i-9j0k-1l2m-3n4o5p6q7r8s",
  "policyId": "9a8b7c6d-5e4f-3g2h-1i0j-9k8l7m6n5o4p",
  "sentBytes": 1024,
  "receivedBytes": 8192,
  "destinationWebCategory": {
    "displayName": "Business",
    "name": "business",
    "group": "Productivity"
  },
  "filteringProfileId": "5f6g7h8i-9j0k-1l2m-3n4o-5p6q7r8s9t0u",
  "filteringProfileName": "Standard Security Profile",
  "policyName": "Internet Traffic Policy",
  "policyRuleName": "Allow Business Websites",
  "initiatingProcessName": "browser.exe",
  "resourceTenantId": "5c3b997a-7ef9-4b2a-a63b-0271df6ace3b",
  "description": "Standard internet traffic",
  "httpMethod": "get",
  "responseCode": 200,
  "operationStatus": "success",
  "popProcessingRegion": "westus"
}
```

## Related content

- [List networkAccessTraffic](https://learn.microsoft.com/en-us/graph/api/networkaccess-logs-list-traffic?view=graph-rest-beta)
