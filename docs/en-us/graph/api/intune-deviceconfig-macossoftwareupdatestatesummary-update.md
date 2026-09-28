<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatestatesummary-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Update macOSSoftwareUpdateStateSummary

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/macOSSoftwareUpdateAccountSummaries/{macOSSoftwareUpdateAccountSummaryId}/categorySummaries/{macOSSoftwareUpdateCategorySummaryId}/updateStateSummaries/{macOSSoftwareUpdateStateSummaryId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | Human readable name of the software update |
| productKey | String | Product key of the software update. |
| updateCategory | [macOSSoftwareUpdateCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategory?view=graph-rest-beta) | Software update category. Possible values are: `critical`, `configurationDataFile`, `firmware`, `other`. |
| updateVersion | String | Version of the software update |
| state | [macOSSoftwareUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestate?view=graph-rest-beta) | State of the software update. Possible values are: `success`, `downloading`, `downloaded`, `installing`, `idle`, `available`, `scheduled`, `downloadFailed`, `downloadInsufficientSpace`, `downloadInsufficientPower`, `downloadInsufficientNetwork`, `installInsufficientSpace`, `installInsufficientPower`, `installFailed`, `commandFailed`. |
| lastUpdatedDateTime | DateTimeOffset | Last date time the report for this device and product key was updated. |

## Response

If successful, this method returns a `200 OK` response code and an updated [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/macOSSoftwareUpdateAccountSummaries/{macOSSoftwareUpdateAccountSummaryId}/categorySummaries/{macOSSoftwareUpdateCategorySummaryId}/updateStateSummaries/{macOSSoftwareUpdateStateSummaryId}
Content-type: application/json
Content-length: 331

{
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateStateSummary",
  "displayName": "Display Name value",
  "productKey": "Product Key value",
  "updateCategory": "configurationDataFile",
  "updateVersion": "Update Version value",
  "state": "downloading",
  "lastUpdatedDateTime": "2017-01-01T00:00:56.8321556-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 380

{
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateStateSummary",
  "id": "9527a1df-a1df-9527-dfa1-2795dfa12795",
  "displayName": "Display Name value",
  "productKey": "Product Key value",
  "updateCategory": "configurationDataFile",
  "updateVersion": "Update Version value",
  "state": "downloading",
  "lastUpdatedDateTime": "2017-01-01T00:00:56.8321556-08:00"
}
```
