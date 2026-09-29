<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-devicecloudlicensing-list-waitingmembers?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# List waitingMembers for device

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) objects for a [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta). This API returns details about allotments where this device is in the waiting room due to license capacity limits.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Device-CloudLicensing.Read | Device-CloudLicensing.Read.All, Device.Read.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Device-CloudLicensing.Read.All | Device.Read.All, Device.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

## HTTP request

```http
GET /devices/{deviceId}/cloudLicensing/waitingMembers
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows how to get all waiting members for a device.

```http
GET https://graph.microsoft.com/beta/devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/waitingMembers?$expand=allotment($select=id,skuId,skuPartNumber)
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "49caea1b-ad15-64f1-70c5-5c5e3563d19c",
      "waitingSinceDateTime": "2024-11-22T17:11:10.6635939+00:00",
      "allotment":
        {
          "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
          "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
          "skuId": "4b9405b0-7788-4568-add1-99614e613b69",
          "skuPartNumber": "EXCHANGESTANDARD"
        }
    }
  ]
}
```
