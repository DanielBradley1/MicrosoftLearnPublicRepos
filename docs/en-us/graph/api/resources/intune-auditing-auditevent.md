<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# auditEvent resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties for Audit Event.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List auditEvents](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0) | [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) collection | List properties and relationships of the [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) objects. |
| [Get auditEvent](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-get?view=graph-rest-1.0) | [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) | Read properties and relationships of the [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) object. |
| [Create auditEvent](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-create?view=graph-rest-1.0) | [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) | Create a new [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) object. |
| [Delete auditEvent](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-delete?view=graph-rest-1.0) | None | Deletes a [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0). |
| [Update auditEvent](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-update?view=graph-rest-1.0) | [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) | Update the properties of a [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent?view=graph-rest-1.0) object. |
| [getAuditCategories function](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-getauditcategories?view=graph-rest-1.0) | String collection |  |
| [getAuditActivityTypes function](https://learn.microsoft.com/en-us/graph/api/intune-auditing-auditevent-getauditactivitytypes?view=graph-rest-1.0) | String collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | Event display name. |
| componentName | String | Component name. |
| actor | [auditActor](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditactor?view=graph-rest-1.0) | AAD user and application that are associated with the audit event. |
| activity | String | Friendly name of the activity. |
| activityDateTime | DateTimeOffset | The date time in UTC when the activity was performed. |
| activityType | String | The type of activity that was being performed. |
| activityOperationType | String | The HTTP operation type of the activity. |
| activityResult | String | The result of the activity. |
| correlationId | Guid | The client request Id that is used to correlate activity within the system. |
| resources | [auditResource](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditresource?view=graph-rest-1.0) collection | Resources being modified. |
| category | String | Audit category. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.auditEvent",
  "id": "String (identifier)",
  "displayName": "String",
  "componentName": "String",
  "actor": {
    "@odata.type": "microsoft.graph.auditActor",
    "type": "String",
    "auditActorType": "String",
    "userPermissions": [
      "String"
    ],
    "applicationId": "String",
    "applicationDisplayName": "String",
    "userPrincipalName": "String",
    "servicePrincipalName": "String",
    "ipAddress": "String",
    "userId": "String"
  },
  "activity": "String",
  "activityDateTime": "String (timestamp)",
  "activityType": "String",
  "activityOperationType": "String",
  "activityResult": "String",
  "correlationId": "Guid",
  "resources": [
    {
      "@odata.type": "microsoft.graph.auditResource",
      "displayName": "String",
      "modifiedProperties": [
        {
          "@odata.type": "microsoft.graph.auditProperty",
          "displayName": "String",
          "oldValue": "String",
          "newValue": "String"
        }
      ],
      "type": "String",
      "auditResourceType": "String",
      "resourceId": "String"
    }
  ],
  "category": "String"
}
```
