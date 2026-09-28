<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create deviceManagementAutopilotPolicyStatusDetail

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementManagedDevices.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/autopilotEvents/{deviceManagementAutopilotEventId}/policyStatusDetails
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the deviceManagementAutopilotPolicyStatusDetail object.

The following table shows the properties that are required when you create the deviceManagementAutopilotPolicyStatusDetail.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object |
| displayName | String | The friendly name of the policy. |
| policyType | [deviceManagementAutopilotPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicytype?view=graph-rest-beta) | The type of policy. The possible values are: `unknown`, `application`, `appModel`, `configurationPolicy`. |
| complianceStatus | [deviceManagementAutopilotPolicyComplianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicycompliancestatus?view=graph-rest-beta) | The policy compliance or enforcement status. Enforcement status takes precedence if it exists. The possible values are: `unknown`, `compliant`, `installed`, `notCompliant`, `notInstalled`, `error`. |
| trackedOnEnrollmentStatus | Boolean | Indicates if this policy was tracked as part of the autopilot bootstrap enrollment sync session |
| lastReportedDateTime | DateTimeOffset | Timestamp of the reported policy status |
| errorCode | Int32 | The errorode associated with the compliance or enforcement status of the policy. Error code for enforcement status takes precedence if it exists. |

## Response

If successful, this method returns a `201 Created` response code and a [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/autopilotEvents/{deviceManagementAutopilotEventId}/policyStatusDetails
Content-type: application/json
Content-length: 314

{
  "@odata.type": "#microsoft.graph.deviceManagementAutopilotPolicyStatusDetail",
  "displayName": "Display Name value",
  "policyType": "application",
  "complianceStatus": "compliant",
  "trackedOnEnrollmentStatus": true,
  "lastReportedDateTime": "2017-01-01T00:00:17.7769392-08:00",
  "errorCode": 9
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 363

{
  "@odata.type": "#microsoft.graph.deviceManagementAutopilotPolicyStatusDetail",
  "id": "dbe093ee-93ee-dbe0-ee93-e0dbee93e0db",
  "displayName": "Display Name value",
  "policyType": "application",
  "complianceStatus": "compliant",
  "trackedOnEnrollmentStatus": true,
  "lastReportedDateTime": "2017-01-01T00:00:17.7769392-08:00",
  "errorCode": 9
}
```
