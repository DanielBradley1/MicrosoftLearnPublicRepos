<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-apps-symanteccodesigningcertificate-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update symantecCodeSigningCertificate

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/symantecCodeSigningCertificate
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the entity. This property is read-only. |
| content | Binary | The Windows Symantec Code-Signing Certificate in the raw data format. |
| status | [certificateStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-certificatestatus?view=graph-rest-beta) | The Cert Status Provisioned or not Provisioned. Possible values are: `notProvisioned`, `provisioned`. |
| password | String | The Password required for .pfx file. |
| subjectName | String | The Subject Name for the cert. |
| subject | String | The Subject value for the cert. |
| issuerName | String | The Issuer Name for the cert. |
| issuer | String | The Issuer value for the cert. |
| expirationDateTime | DateTimeOffset | The Cert Expiration Date. |
| uploadDateTime | DateTimeOffset | The Type of the CodeSigning Cert as Symantec Cert. |

## Response

If successful, this method returns a `200 OK` response code and an updated [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceAppManagement/symantecCodeSigningCertificate
Content-type: application/json
Content-length: 421

{
  "@odata.type": "#microsoft.graph.symantecCodeSigningCertificate",
  "content": "Y29udGVudA==",
  "status": "provisioned",
  "password": "Password value",
  "subjectName": "Subject Name value",
  "subject": "Subject value",
  "issuerName": "Issuer Name value",
  "issuer": "Issuer value",
  "expirationDateTime": "2016-12-31T23:57:57.2481234-08:00",
  "uploadDateTime": "2016-12-31T23:58:46.5747426-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 470

{
  "@odata.type": "#microsoft.graph.symantecCodeSigningCertificate",
  "id": "00ffe83e-e83e-00ff-3ee8-ff003ee8ff00",
  "content": "Y29udGVudA==",
  "status": "provisioned",
  "password": "Password value",
  "subjectName": "Subject Name value",
  "subject": "Subject value",
  "issuerName": "Issuer Name value",
  "issuer": "Issuer value",
  "expirationDateTime": "2016-12-31T23:57:57.2481234-08:00",
  "uploadDateTime": "2016-12-31T23:58:46.5747426-08:00"
}
```
