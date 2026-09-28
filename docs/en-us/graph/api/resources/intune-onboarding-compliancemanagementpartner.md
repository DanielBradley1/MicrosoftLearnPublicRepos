<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# complianceManagementPartner resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Compliance management partner for all platforms

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List complianceManagementPartners](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-compliancemanagementpartner-list?view=graph-rest-1.0) | [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) collection | List properties and relationships of the [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) objects. |
| [Get complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-compliancemanagementpartner-get?view=graph-rest-1.0) | [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) | Read properties and relationships of the [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) object. |
| [Create complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-compliancemanagementpartner-create?view=graph-rest-1.0) | [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) | Create a new [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) object. |
| [Delete complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-compliancemanagementpartner-delete?view=graph-rest-1.0) | None | Deletes a [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0). |
| [Update complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-compliancemanagementpartner-update?view=graph-rest-1.0) | [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) | Update the properties of a [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner?view=graph-rest-1.0) object. |

## Properties

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

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.complianceManagementPartner",
  "id": "String (identifier)",
  "lastHeartbeatDateTime": "String (timestamp)",
  "partnerState": "String",
  "displayName": "String",
  "macOsOnboarded": true,
  "androidOnboarded": true,
  "iosOnboarded": true,
  "macOsEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "String",
        "entraObjectId": "String"
      }
    }
  ],
  "androidEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "String",
        "entraObjectId": "String"
      }
    }
  ],
  "iosEnrollmentAssignments": [
    {
      "@odata.type": "microsoft.graph.complianceManagementPartnerAssignment",
      "target": {
        "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
        "targetType": "String",
        "entraObjectId": "String"
      }
    }
  ]
}
```
