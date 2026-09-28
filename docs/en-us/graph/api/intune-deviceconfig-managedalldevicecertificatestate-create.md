<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-managedalldevicecertificatestate-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create managedAllDeviceCertificateState

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) object.

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
POST /deviceManagement/deviceConfigurationsAllManagedDeviceCertificateStates
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the managedAllDeviceCertificateState object.

The following table shows the properties that are required when you create the managedAllDeviceCertificateState.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| certificateRevokeStatus | [certificateRevocationStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-certificaterevocationstatus?view=graph-rest-beta) | Revoke status. Possible values are: `none`, `pending`, `issued`, `failed`, `revoked`. |
| certificateRevokeStatusLastChangeDateTime | DateTimeOffset | The time the revoke status was last changed |
| managedDeviceDisplayName | String | Device display name |
| userPrincipalName | String | User principal name |
| certificateExpirationDateTime | DateTimeOffset | Certificate expiry date |
| certificateIssuerName | String | Issuer |
| certificateThumbprint | String | Thumbprint |
| certificateSerialNumber | String | Serial number |
| certificateSubjectName | String | Certificate subject name |
| certificateKeyUsages | Int32 | Key Usage |
| certificateExtendedKeyUsages | String | Enhanced Key Usage |
| certificateIssuanceDateTime | DateTimeOffset | Issuance date |

## Response

If successful, this method returns a `201 Created` response code and a [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceConfigurationsAllManagedDeviceCertificateStates
Content-type: application/json
Content-length: 820

{
  "@odata.type": "#microsoft.graph.managedAllDeviceCertificateState",
  "certificateRevokeStatus": "pending",
  "certificateRevokeStatusLastChangeDateTime": "2016-12-31T23:59:34.9547208-08:00",
  "managedDeviceDisplayName": "Managed Device Display Name value",
  "userPrincipalName": "User Principal Name value",
  "certificateExpirationDateTime": "2017-01-01T00:02:14.9489247-08:00",
  "certificateIssuerName": "Certificate Issuer Name value",
  "certificateThumbprint": "Certificate Thumbprint value",
  "certificateSerialNumber": "Certificate Serial Number value",
  "certificateSubjectName": "Certificate Subject Name value",
  "certificateKeyUsages": 4,
  "certificateExtendedKeyUsages": "Certificate Extended Key Usages value",
  "certificateIssuanceDateTime": "2016-12-31T23:59:41.5044473-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 869

{
  "@odata.type": "#microsoft.graph.managedAllDeviceCertificateState",
  "id": "987c6a17-6a17-987c-176a-7c98176a7c98",
  "certificateRevokeStatus": "pending",
  "certificateRevokeStatusLastChangeDateTime": "2016-12-31T23:59:34.9547208-08:00",
  "managedDeviceDisplayName": "Managed Device Display Name value",
  "userPrincipalName": "User Principal Name value",
  "certificateExpirationDateTime": "2017-01-01T00:02:14.9489247-08:00",
  "certificateIssuerName": "Certificate Issuer Name value",
  "certificateThumbprint": "Certificate Thumbprint value",
  "certificateSerialNumber": "Certificate Serial Number value",
  "certificateSubjectName": "Certificate Subject Name value",
  "certificateKeyUsages": 4,
  "certificateExtendedKeyUsages": "Certificate Extended Key Usages value",
  "certificateIssuanceDateTime": "2016-12-31T23:59:41.5044473-08:00"
}
```
