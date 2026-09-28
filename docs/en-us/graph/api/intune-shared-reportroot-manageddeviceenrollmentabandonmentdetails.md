<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-manageddeviceenrollmentabandonmentdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-10 -->

# managedDeviceEnrollmentAbandonmentDetails function

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Metadata for Enrollment abandonment details report

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

```
    ## Permissions
```

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All |
| **Troublshooting** | DeviceManagementManagedDevices.ReadWrite.All, DeviceManagementManagedDevices.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All |
| **Troublshooting** | DeviceManagementManagedDevices.ReadWrite.All, DeviceManagementManagedDevices.Read.All |

## HTTP Request

```http
GET /reports/managedDeviceEnrollmentAbandonmentDetails
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request URL, provide the following query parameters with values. The following table shows the parameters that can be used with this function.

| Property | Type | Description |
| :--- | :--- | :--- |
| skip | Int32 |  |
| top | Int32 |  |
| filter | String |  |
| skipToken | String |  |

## Response

If successful, this function returns a `200 OK` response code and a [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-report?view=graph-rest-beta) in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentAbandonmentDetails(skip=4,top=3,filter='parameterValue',skipToken='parameterValue')
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 123

{
  "value": {
    "@odata.type": "microsoft.graph.report",
    "content": "<Unknown Primitive Type Edm.Stream>"
  }
}
```
