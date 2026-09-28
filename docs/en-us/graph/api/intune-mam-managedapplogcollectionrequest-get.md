<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapplogcollectionrequest-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Get managedAppLogCollectionRequest

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Read properties and relationships of the [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
GET /deviceAppManagement/managedAppRegistrations/{managedAppRegistrationId}/managedAppLogCollectionRequests/{managedAppLogCollectionRequestId}
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceAppManagement/managedAppRegistrations/{managedAppRegistrationId}/managedAppLogCollectionRequests/{managedAppLogCollectionRequestId}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 905

{
  "value": {
    "@odata.type": "#microsoft.graph.managedAppLogCollectionRequest",
    "id": "95b5bd26-bd26-95b5-26bd-b59526bdb595",
    "managedAppRegistrationId": "Managed App Registration Id value",
    "status": "Status value",
    "requestedBy": "Requested By value",
    "requestedByUserPrincipalName": "Requested By User Principal Name value",
    "requestedDateTime": "2017-01-01T00:01:49.2071853-08:00",
    "completedDateTime": "2016-12-31T23:58:52.3534526-08:00",
    "userLogUploadConsent": "declined",
    "uploadedLogs": [
      {
        "@odata.type": "microsoft.graph.managedAppLogUpload",
        "managedAppComponent": "Managed App Component value",
        "managedAppComponentDescription": "Managed App Component Description value",
        "status": "inProgress",
        "referenceId": "Reference Id value"
      }
    ],
    "version": "Version value"
  }
}
```
