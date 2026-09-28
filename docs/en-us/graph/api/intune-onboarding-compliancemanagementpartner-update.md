<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-onboarding-compliancemanagementpartner-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update complianceManagementPartner

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) object.

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
PATCH /deviceManagement/complianceManagementPartners/{complianceManagementPartnerId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the entity |
| lastHeartbeatDateTime | DateTimeOffset | Timestamp of last heartbeat after admin onboarded to the compliance management partner |
| partnerState | [deviceManagementPartnerTenantState](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartnertenantstate?view=graph-rest-1.0) | Partner state of this tenant. The possible values are: `unknown`, `unavailable`, `enabled`, `terminated`, `rejected`, `unresponsive`. |
| displayName | String | Partner display name |
| macOsOnboarded | Boolean | Partner onboarded for Mac devices. |
| androidOnboarded | Boolean | Partner onboarded for Android devices. |
| iosOnboarded | Boolean | Partner onboarded for ios devices. |
| macOsEnrollmentAssignments | [complianceManagementPartnerAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartnerassignment?view=graph-rest-1.0) collection | User groups which enroll Mac devices through partner. |
| androidEnrollmentAssignments | [complianceManagementPartnerAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartnerassignment?view=graph-rest-1.0) collection | User groups which enroll Android devices through partner. |
| iosEnrollmentAssignments | [complianceManagementPartnerAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartnerassignment?view=graph-rest-1.0) collection | User groups which enroll ios devices through partner. |

## Response

If successful, this method returns a `200 OK` response code and an updated [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/complianceManagementPartners/{complianceManagementPartnerId}
Content-type: application/json
Content-length: 1237

{
  "@odata.type": "#microsoft.graph.complianceManagementPartner",
  "lastHeartbeatDateTime": "2016-12-31T23:59:37.9174975-08:00",
  "partnerState": "unavailable",
  "displayName": "Display Name value",
  "macOsOnboarded": true,
  "androidOnboarded": true,
  "iosOnboarded": true,
  "macOsEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "user",
        "entraObjectId": "Entra Object Id value"
      }
    }
  ],
  "androidEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "user",
        "entraObjectId": "Entra Object Id value"
      }
    }
  ],
  "iosEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
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
Content-Length: 1286

{
  "@odata.type": "#microsoft.graph.complianceManagementPartner",
  "id": "d6d46d0d-6d0d-d6d4-0d6d-d4d60d6dd4d6",
  "lastHeartbeatDateTime": "2016-12-31T23:59:37.9174975-08:00",
  "partnerState": "unavailable",
  "displayName": "Display Name value",
  "macOsOnboarded": true,
  "androidOnboarded": true,
  "iosOnboarded": true,
  "macOsEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "user",
        "entraObjectId": "Entra Object Id value"
      }
    }
  ],
  "androidEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "user",
        "entraObjectId": "Entra Object Id value"
      }
    }
  ],
  "iosEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "user",
        "entraObjectId": "Entra Object Id value"
      }
    }
  ]
}
```
