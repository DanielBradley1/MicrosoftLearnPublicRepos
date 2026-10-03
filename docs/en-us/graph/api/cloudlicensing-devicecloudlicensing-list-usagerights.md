<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-devicecloudlicensing-list-usagerights?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# List usageRights for device

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) objects granted to a [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta). This API returns details about licenses that are directly assigned to a device and those licenses transitively assigned through membership in licensed groups.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudLicensing-UsageRights.Read | CloudLicensing-UsageRights.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudLicensing-UsageRights.Read.All | CloudLicensing-UsageRights.ReadWrite.All |

## HTTP request

```http
GET /devices/{deviceId}/cloudLicensing/usageRights
```

## Optional query parameters

This method supports the `$select`, `$top`, `$expand`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The following examples show how to get usage rights information for devices based on specific filters:

```http
GET /devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/usageRights?$filter=skuId eq a0cfb9b5-427c-4d42-9e6d-6727c6bbd8b5
GET /devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/usageRights?$filter=skuId in (a0cfb9b5-427c-4d42-9e6d-6727c6bbd8b5, 639dec6b-bb19-468b-871c-c5c441c4b0cb)
GET /devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/usageRights?$filter=services/any(c:c/planId eq b7786c33-f595-4df5-bed7-9a2c8622df78)
GET /devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/usageRights?$filter=services/any(c:c/planId in (b7786c33-f595-4df5-bed7-9a2c8622df78, f446866a-4b4c-492e-907a-998b3fde5a81))
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) objects in the response body.

## Examples

### Example 1: Get all usage rights for a device

The following example shows how to get all usage rights granted to a device.

#### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/beta/devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/usageRights
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
      "id": "a8d33537-2833-4f1c-8797-7aa891e15723",
      "skuId": "a0cfb9b5-427c-4d42-9e6d-6727c6bbd8b5",
      "skuPartNumber": "FABRIKAM_DEVICE",
      "services": [
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,device,group",
          "planId": "b7786c33-f595-4df5-bed7-9a2c8622df78",
          "planName": "FABRIKAM_DESKTOP"
        },
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,device,group",
          "planId": "f446866a-4b4c-492e-907a-998b3fde5a81",
          "planName": "FABRIKAM_REMOTE"
        },
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,device,group",
          "planId": "f08373fb-2530-4f97-8aa4-f424f071780d",
          "planName": "FABRIKAM_TASKS"
        }
      ]
    }
  ]
}
```

### Example 2: Get all usage rights for a device with a specific SKU

The following example shows how to get all usage rights granted to a device for a specific SKU.

#### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/beta/devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/usageRights?$filter=skuId eq a0cfb9b5-427c-4d42-9e6d-6727c6bbd8b5
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
      "id": "a8d33537-2833-4f1c-8797-7aa891e15723",
      "skuId": "a0cfb9b5-427c-4d42-9e6d-6727c6bbd8b5",
      "skuPartNumber": "FABRIKAM_DEVICE",
      "services": [
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,device,group",
          "planId": "b7786c33-f595-4df5-bed7-9a2c8622df78",
          "planName": "FABRIKAM_DESKTOP"
        },
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,device,group",
          "planId": "f446866a-4b4c-492e-907a-998b3fde5a81",
          "planName": "FABRIKAM_REMOTE"
        },
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,device,group",
          "planId": "f08373fb-2530-4f97-8aa4-f424f071780d",
          "planName": "FABRIKAM_TASKS"
        }
      ]
    }
  ]
}
```
