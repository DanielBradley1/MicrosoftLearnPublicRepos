<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-epmgraphapiservice-privilegemanagementelevationrequest-getallelevationrequests?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# getAllElevationRequests action

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/elevationRequests/{privilegeManagementElevationRequestId}/getAllElevationRequests
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [privilegeManagementElevationRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-epmgraphapiservice-privilegemanagementelevationrequest?view=graph-rest-beta) collection in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/elevationRequests/{privilegeManagementElevationRequestId}/getAllElevationRequests
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1564

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.privilegeManagementElevationRequest",
      "id": "3df245af-45af-3df2-af45-f23daf45f23d",
      "requestedByUserId": "Requested By User Id value",
      "requestedOnDeviceId": "Requested On Device Id value",
      "requestedByUserPrincipalName": "Requested By User Principal Name value",
      "deviceName": "Device Name value",
      "requestCreatedDateTime": "2017-01-01T00:00:35.2743776-08:00",
      "requestLastModifiedDateTime": "2016-12-31T23:58:50.6194179-08:00",
      "requestJustification": "Request Justification value",
      "applicationDetail": {
        "@odata.type": "microsoft.graph.elevationRequestApplicationDetail",
        "fileHash": "File Hash value",
        "fileName": "File Name value",
        "filePath": "File Path value",
        "fileDescription": "File Description value",
        "publisherName": "Publisher Name value",
        "publisherCert": "Publisher Cert value",
        "productName": "Product Name value",
        "productInternalName": "Product Internal Name value",
        "productVersion": "Product Version value"
      },
      "status": "pending",
      "reviewCompletedByUserId": "Review Completed By User Id value",
      "reviewCompletedByUserPrincipalName": "Review Completed By User Principal Name value",
      "reviewCompletedDateTime": "2016-12-31T23:59:07.609607-08:00",
      "requestExpiryDateTime": "2017-01-01T00:02:44.7662751-08:00",
      "reviewerJustification": "Reviewer Justification value"
    }
  ]
}
```
