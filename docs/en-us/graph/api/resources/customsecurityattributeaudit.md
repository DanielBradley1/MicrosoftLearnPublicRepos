<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeaudit?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# customSecurityAttributeAudit resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom security attribute audit log.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/auditlogroot-list-customsecurityattributeaudits?view=graph-rest-beta) | [customSecurityAttributeAudit](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeaudit?view=graph-rest-beta) collection | List the custom security attribute audit items in the collection and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customsecurityattributeaudit-get?view=graph-rest-beta) | [customSecurityAttributeAudit](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeaudit?view=graph-rest-beta) | Get a specific custom security attribute audit item and its properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityDateTime | DateTimeOffset | Indicates the date and time the activity was performed. The Timestamp type is always in UTC time. For example, midnight UTC on Jan 1, 2024 is `2024-01-01T00:00:00Z`. Supports `$filter` \(`eq`, `ge`, `le`\). |
| activityDisplayName | String | Indicates the activity name or the operation name. For example: "Add custom security attribute definition in an attribute set" or "Update attribute values assigned to a user." For a list of activities logged, refer to [Microsoft Entra audit log categories and activities](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/reference-audit-activities). Supports `$filter` \(`eq`, `startswith`\). |
| additionalDetails | [keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-beta) collection | Indicates additional details on the activity. |
| category | String | Indicates the resource category that's targeted by the activity. Custom security attribute activities are logged in a single category: `AttributeManagement`. |
| correlationId | String | Indicates a unique ID that helps correlate activities that span across various services. Can be used to trace logs across services. |
| id | String | Indicates the unique ID for the activity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| initiatedBy | [auditActivityInitiator](https://learn.microsoft.com/en-us/graph/api/resources/auditactivityinitiator?view=graph-rest-beta) | Indicates information about the user or app initiated the activity. Supports `$filter` \(`eq`\) for **user/id**, **user/displayName**, **user/userPrincipalName**, **app/appId**, **app/displayName**; and `$filter` \(`startswith`\) for **user/userPrincipalName**. |
| loggedByService | String | Indicates information on which service initiated the activity. For example: `Core Directory`. Supports `$filter` \(`eq`\). |
| operationType | String | Indicates the type of operation that was performed. The possible values include but aren't limited to the following: `Add`, `Assign`, `Update`, `Unassign`, and `Delete`. |
| result | operationResult | Indicates the result of the activity. The possible values are: `success`, `failure`, `timeout`, `unknownFutureValue`. |
| resultReason | String | Indicates the reason for failure if the **result** is `failure` or `timeout`. |
| targetResources | [targetResource](https://learn.microsoft.com/en-us/graph/api/resources/targetresource?view=graph-rest-beta) collection | Indicates information on which resource was changed due to the activity. The target resource type can be `User`, `App`, or `Other`. Supports `$filter` \(`eq`\) for **id** and **displayName**; and `$filter` \(`startswith`\) for **displayName**. |
| userAgent | String | Type of user agent used by a user in the activity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customSecurityAttributeAudit",
  "id": "String (identifier)",
  "category": "String",
  "correlationId": "String",
  "result": "String",
  "resultReason": "String",
  "activityDisplayName": "String",
  "activityDateTime": "String (timestamp)",
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
  ]
}
```
