<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementpartner-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update deviceManagementPartner

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) object.

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
PATCH /deviceManagement/deviceManagementPartners/{deviceManagementPartnerId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the entity |
| lastHeartbeatDateTime | DateTimeOffset | Timestamp of last heartbeat after admin enabled option Connect to Device management Partner |
| partnerState | [deviceManagementPartnerTenantState](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartnertenantstate?view=graph-rest-1.0) | Partner state of this tenant. The possible values are: `unknown`, `unavailable`, `enabled`, `terminated`, `rejected`, `unresponsive`. |
| partnerAppType | [deviceManagementPartnerAppType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartnerapptype?view=graph-rest-1.0) | Partner App type. The possible values are: `unknown`, `singleTenantApp`, `multiTenantApp`. |
| singleTenantAppId | String | Partner Single tenant App id |
| displayName | String | Partner display name |
| isConfigured | Boolean | Whether device management partner is configured or not |
| whenPartnerDevicesWillBeRemovedDateTime | DateTimeOffset | DateTime in UTC when PartnerDevices will be removed |
| whenPartnerDevicesWillBeMarkedAsNonCompliantDateTime | DateTimeOffset | DateTime in UTC when PartnerDevices will be marked as NonCompliant |
| groupsRequiringPartnerEnrollment | [deviceManagementPartnerAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartnerassignment?view=graph-rest-1.0) collection | User groups that specifies whether enrollment is through partner. |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/deviceManagementPartners/{deviceManagementPartnerId}
Content-type: application/json
Content-length: 820

{
  "@odata.type": "#microsoft.graph.deviceManagementPartner",
  "lastHeartbeatDateTime": "2016-12-31T23:59:37.9174975-08:00",
  "partnerState": "unavailable",
  "partnerAppType": "singleTenantApp",
  "singleTenantAppId": "Single Tenant App Id value",
  "displayName": "Display Name value",
  "isConfigured": true,
  "whenPartnerDevicesWillBeRemovedDateTime": "2016-12-31T23:56:38.2655023-08:00",
  "whenPartnerDevicesWillBeMarkedAsNonCompliantDateTime": "2016-12-31T23:58:42.2131231-08:00",
  "groupsRequiringPartnerEnrollment": [
    {
      "@odata.type": "microsoft.graph.deviceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "user",
        "entraObjectId": "Entra Object Id value"
      }
    }
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 869

{
  "@odata.type": "#microsoft.graph.deviceManagementPartner",
  "id": "d21e377a-377a-d21e-7a37-1ed27a371ed2",
  "lastHeartbeatDateTime": "2016-12-31T23:59:37.9174975-08:00",
  "partnerState": "unavailable",
  "partnerAppType": "singleTenantApp",
  "singleTenantAppId": "Single Tenant App Id value",
  "displayName": "Display Name value",
  "isConfigured": true,
  "whenPartnerDevicesWillBeRemovedDateTime": "2016-12-31T23:56:38.2655023-08:00",
  "whenPartnerDevicesWillBeMarkedAsNonCompliantDateTime": "2016-12-31T23:58:42.2131231-08:00",
  "groupsRequiringPartnerEnrollment": [
    {
      "@odata.type": "microsoft.graph.deviceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "user",
        "entraObjectId": "Entra Object Id value"
      }
    }
  ]
}
```
