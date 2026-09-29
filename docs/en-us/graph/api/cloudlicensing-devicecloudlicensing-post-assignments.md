<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-devicecloudlicensing-post-assignments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Create assignment for device

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection for a [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta).

An assignment must always have a direct relationship to an allotment and to a user, group, or device. If an assignment is created by posting to the **assignments** collection of a device, located at `/devices/{deviceId}/cloudLicensing/assignments`, the **allotment** relationship must be established in the request body. Assignments can also be created by posting to the **assignments** collection of an organization, the **assignments** collection of an allotment, or the **assignments** collection of a user or group.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudLicensing-Assignment.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudLicensing-Assignment.ReadWrite.All | Not available. |

## HTTP request

```http
POST /devices/{deviceId}/cloudLicensing/assignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object.

You can specify the following properties when you create an **assignment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledServicePlanIds | Guid collection | The list of disabled service plans for this assignment. An empty list indicates that all services are enabled. Required. Not nullable. |

You can specify the following relationships when you create an **assignment**.

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allotment | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) | The allotment from which licenses are assigned. Required. Not nullable. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/assignments
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "allotment@odata.bind": "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi",
  "disabledServicePlanIds": [
    "bed136c6-b799-4462-824d-fc045d3a9d25"
  ]
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "disabledServicePlanIds": [
    "bed136c6-b799-4462-824d-fc045d3a9d25"
  ]
}
```
