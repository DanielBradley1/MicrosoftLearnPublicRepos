<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionapplearningsummary-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update windowsInformationProtectionAppLearningSummary

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/windowsInformationProtectionAppLearningSummaries/{windowsInformationProtectionAppLearningSummaryId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the WindowsInformationProtectionAppLearningSummary. |
| applicationName | String | Application Name |
| applicationType | [applicationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-applicationtype?view=graph-rest-1.0) | Application Type. The possible values are: `universal`, `desktop`. |
| deviceCount | Int32 | Device Count |

## Response

If successful, this method returns a `200 OK` response code and an updated [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/windowsInformationProtectionAppLearningSummaries/{windowsInformationProtectionAppLearningSummaryId}
Content-type: application/json
Content-length: 191

{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionAppLearningSummary",
  "applicationName": "Application Name value",
  "applicationType": "desktop",
  "deviceCount": 11
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 240

{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionAppLearningSummary",
  "id": "063baf50-af50-063b-50af-3b0650af3b06",
  "applicationName": "Application Name value",
  "applicationType": "desktop",
  "deviceCount": 11
}
```
