<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-datasharingconsent-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update dataSharingConsent

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/dataSharingConsents/{dataSharingConsentId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The data sharing consent Id |
| serviceDisplayName | String | The display name of the service work flow |
| termsUrl | String | The TermsUrl for the data sharing consent |
| granted | Boolean | The granted state for the data sharing consent |
| grantDateTime | DateTimeOffset | The time consent was granted for this account |
| grantedByUpn | String | The Upn of the user that granted consent for this account |
| grantedByUserId | String | The UserId of the user that granted consent for this account |

## Response

If successful, this method returns a `200 OK` response code and an updated [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/dataSharingConsents/{dataSharingConsentId}
Content-type: application/json
Content-length: 333

{
  "@odata.type": "#microsoft.graph.dataSharingConsent",
  "serviceDisplayName": "Service Display Name value",
  "termsUrl": "https://example.com/termsUrl/",
  "granted": true,
  "grantDateTime": "2016-12-31T23:59:55.7154191-08:00",
  "grantedByUpn": "Granted By Upn value",
  "grantedByUserId": "Granted By User Id value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 382

{
  "@odata.type": "#microsoft.graph.dataSharingConsent",
  "id": "333387f7-87f7-3333-f787-3333f7873333",
  "serviceDisplayName": "Service Display Name value",
  "termsUrl": "https://example.com/termsUrl/",
  "granted": true,
  "grantDateTime": "2016-12-31T23:59:55.7154191-08:00",
  "grantedByUpn": "Granted By Upn value",
  "grantedByUserId": "Granted By User Id value"
}
```
