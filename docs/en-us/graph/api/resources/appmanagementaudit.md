<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appmanagementaudit?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# appManagementAudit resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Entra application management audit log entry and the app management policy restrictions applied to the activity.

Inherits from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List appManagementAudit objects](https://learn.microsoft.com/en-us/graph/api/appmanagementaudit-list?view=graph-rest-beta) | [appManagementAudit](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementaudit?view=graph-rest-beta) collection | Get app management audit logs and their properties. |
| [Get appManagementAudit](https://learn.microsoft.com/en-us/graph/api/appmanagementaudit-get?view=graph-rest-beta) | [appManagementAudit](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementaudit?view=graph-rest-beta) | Get an app management audit log and its properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityDateTime | DateTimeOffset | The date and time when the activity was performed. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| activityDisplayName | String | The activity or operation name. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| additionalDetails | [keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-beta) collection | Additional details about the activity. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| appliedAppManagementPolicyRestrictions | [appliedAppManagementPolicyRestriction](https://learn.microsoft.com/en-us/graph/api/resources/appliedappmanagementpolicyrestriction?view=graph-rest-beta) collection | Details of the app management policy restrictions applied to the activity. Supports `$filter` \(`eq`\). |
| category | String | The resource category targeted by the activity. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| correlationId | String | The unique identifier used to correlate activities that span multiple services. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| id | String | The unique identifier for the activity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| initiatedBy | [auditActivityInitiator](https://learn.microsoft.com/en-us/graph/api/resources/auditactivityinitiator?view=graph-rest-beta) | The user or app that initiated the activity. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| loggedByService | String | The service that initiated the activity. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| operationType | String | The type of operation that was performed. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| result | operationResult | The result of the activity. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). The possible values are: `success`, `failure`, `timeout`, `unknownFutureValue`. |
| resultReason | String | The reason for a failure when **result** is `failure` or `timeout`. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| targetResources | [targetResource](https://learn.microsoft.com/en-us/graph/api/resources/targetresource?view=graph-rest-beta) collection | Information about the resources changed by the activity. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |
| userAgent | String | The user agent used for the activity. Inherited from [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appManagementAudit",
  "id": "String",
  "category": "String",
  "correlationId": "String",
  "result": "String",
  "resultReason": "String",
  "activityDisplayName": "String",
  "activityDateTime": "DateTimeOffset",
  "loggedByService": "String",
  "operationType": "String",
  "initiatedBy": {
    "@odata.type": "microsoft.graph.auditActivityInitiator"
  },
  "targetResources": [
    {
      "@odata.type": "microsoft.graph.targetResource"
    }
  ],
  "userAgent": "String",
  "additionalDetails": [
    {
      "@odata.type": "microsoft.graph.keyValue"
    }
  ],
  "appliedAppManagementPolicyRestrictions": [
    {
      "@odata.type": "microsoft.graph.appliedAppManagementPolicyRestriction"
    }
  ]
}
```
