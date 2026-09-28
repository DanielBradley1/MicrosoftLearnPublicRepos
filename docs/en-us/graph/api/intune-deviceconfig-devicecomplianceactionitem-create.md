<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceactionitem-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Create deviceComplianceActionItem

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) object.

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
POST /deviceManagement/deviceCompliancePolicies/{deviceCompliancePolicyId}/scheduledActionsForRule/{deviceComplianceScheduledActionForRuleId}/scheduledActionConfigurations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the deviceComplianceActionItem object.

The following table shows the properties that are required when you create the deviceComplianceActionItem.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| gracePeriodHours | Int32 | Number of hours to wait till the action will be enforced. Valid values 0 to 8760 |
| actionType | [deviceComplianceActionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactiontype?view=graph-rest-1.0) | What action to take. The possible values are: `noAction`, `notification`, `block`, `retire`, `wipe`, `removeResourceAccessProfiles`, `pushNotification`. |
| notificationTemplateId | String | What notification Message template to use |
| notificationMessageCCList | String collection | A list of group IDs to speicify who to CC this notification message to. |

## Response

If successful, this method returns a `201 Created` response code and a [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/deviceCompliancePolicies/{deviceCompliancePolicyId}/scheduledActionsForRule/{deviceComplianceScheduledActionForRuleId}/scheduledActionConfigurations
Content-type: application/json
Content-length: 271

{
  "@odata.type": "#microsoft.graph.deviceComplianceActionItem",
  "gracePeriodHours": 0,
  "actionType": "notification",
  "notificationTemplateId": "Notification Template Id value",
  "notificationMessageCCList": [
    "Notification Message CCList value"
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 320

{
  "@odata.type": "#microsoft.graph.deviceComplianceActionItem",
  "id": "e01a1893-1893-e01a-9318-1ae093181ae0",
  "gracePeriodHours": 0,
  "actionType": "notification",
  "notificationTemplateId": "Notification Template Id value",
  "notificationMessageCCList": [
    "Notification Message CCList value"
  ]
}
```
