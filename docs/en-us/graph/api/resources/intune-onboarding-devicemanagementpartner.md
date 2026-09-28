<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementPartner resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity which represents a connection to device management partner.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementPartners](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementpartner-list?view=graph-rest-1.0) | [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) collection | List properties and relationships of the [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) objects. |
| [Get deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementpartner-get?view=graph-rest-1.0) | [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) | Read properties and relationships of the [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) object. |
| [Create deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementpartner-create?view=graph-rest-1.0) | [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) | Create a new [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) object. |
| [Delete deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementpartner-delete?view=graph-rest-1.0) | None | Deletes a [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0). |
| [Update deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementpartner-update?view=graph-rest-1.0) | [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) | Update the properties of a [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner?view=graph-rest-1.0) object. |
| [terminate action](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementpartner-terminate?view=graph-rest-1.0) | None |  |

## Properties

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

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementPartner",
  "id": "String (identifier)",
  "lastHeartbeatDateTime": "String (timestamp)",
  "partnerState": "String",
  "partnerAppType": "String",
  "singleTenantAppId": "String",
  "displayName": "String",
  "isConfigured": true,
  "whenPartnerDevicesWillBeRemovedDateTime": "String (timestamp)",
  "whenPartnerDevicesWillBeMarkedAsNonCompliantDateTime": "String (timestamp)",
  "groupsRequiringPartnerEnrollment": [
    {
      "@odata.type": "microsoft.graph.deviceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "String",
        "entraObjectId": "String"
      }
    }
  ]
}
```
