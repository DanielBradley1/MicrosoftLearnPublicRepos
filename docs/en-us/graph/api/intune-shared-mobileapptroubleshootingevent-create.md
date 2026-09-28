<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapptroubleshootingevent-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# Create mobileAppTroubleshootingEvent

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) object.

```
    ## Permissions
```

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) |  |
| **Device management** | DeviceManagementManagedDevices.ReadWrite.All |
| **Troubleshooting** | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application |  |
| **Device management** | DeviceManagementManagedDevices.ReadWrite.All |
| **Troubleshooting** | DeviceManagementManagedDevices.ReadWrite.All |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## HTTP Request

```http
POST /deviceManagement/mobileAppTroubleshootingEvents
POST /users/{usersId}/mobileAppTroubleshootingEvents
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the mobileAppTroubleshootingEvent object.

The following table shows the properties that are required when you create the mobileAppTroubleshootingEvent.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |
| **Troubleshooting** |  |  |
| additionalInformation | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyvaluepair?view=graph-rest-beta) collection | A set of string key and string value pairs which provides additional information on the Troubleshooting event. |
| applicationId | String | Intune application identifier. |
| correlationId | String | ID used for tracing the failure in the service. |
| eventDateTime | DateTimeOffset | Time when the event occurred . |
| eventName | String | Event Name corresponding to the Troubleshooting Event. Optional. |
| history | [mobileAppTroubleshootingHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileapptroubleshootinghistoryitem?view=graph-rest-beta) collection | Intune Mobile Application Troubleshooting History Item |
| managedDeviceIdentifier | String | Device identifier created or collected by Intune. |
| troubleshootingErrorDetails | [deviceManagementTroubleshootingErrorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingerrordetails?view=graph-rest-beta) | Object containing detailed information about the error and its remediation. |
| userId | String | Identifier for the user that tried to enroll the device. |

## Response

If successful, this method returns a `201 Created` response code and a [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/mobileAppTroubleshootingEvents
Content-type: application/json
Content-length: 71

{
  "@odata.type": "#microsoft.graph.mobileAppTroubleshootingEvent"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 120

{
  "@odata.type": "#microsoft.graph.mobileAppTroubleshootingEvent",
  "id": "77943c10-3c10-7794-103c-9477103c9477"
}
```
