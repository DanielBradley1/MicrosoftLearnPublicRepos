<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-auditevent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# auditEvent resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit event for managed tenants in Microsoft 365 Lighthouse.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-auditevents?view=graph-rest-beta) | [microsoft.graph.managedTenants.auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-auditevent?view=graph-rest-beta) collection | Get a list of the [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-auditevent?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/managedtenants-auditevent-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-auditevent?view=graph-rest-beta) | Read the properties and relationships of an [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-auditevent?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | String | A string that uniquely represents the operation that occurred. Required. Read-only. |
| activityDateTime | DateTimeOffset | The time when the activity occurred. Required. Read-only. |
| activityId | String | The identifier of the activity request that made the audit event. Required. Read-only. |
| category | String | A category that represents a logical grouping of activities. Required. Read-only. |
| httpVerb | String | The HTTP verb that was used when making the API request. Required. Read-only. |
| id | String | The unique identifier of the audit event. Required. Read-only. |
| initiatedByAppId | String | The identifier of the app that was used to make the request. Required. Read-only. |
| initiatedByUpn | String | The UPN of the user who initiated the activity. Required. Read-only. |
| initiatedByUserId | String | The identifier of the user who initiated the activity. Required. Read-only. |
| ipAddress | String | The IP address of where the activity was initiated. This may be an IPv4 or IPv6 address. Required. Read-only. |
| requestBody | String | The raw HTTP request body. Some sensitive information may be removed. |
| requestUrl | String | The raw HTTP request URL. Required. Read-only. |
| tenantIds | String | The collection of Microsoft Entra tenant identifiers for the [managed tenants](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) that were affected by a change, and is formatted as a list of comma-separated values. Required. Read-only. |
| tenantNames | String | The collection of tenant names that were affected by a change, and is formatted as a list of comma-separated values. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.auditEvent",
  "activity": "String",
  "activityDateTime": "String (timestamp)",
  "activityId": "String",
  "category": "String",
  "httpVerb": "String",
  "id": "String (identifier)",
  "initiatedByAppId": "String",
  "initiatedByUpn": "String",
  "initiatedByUserId": "String",
  "ipAddress": "String",
  "requestBody": "String",
  "requestUrl": "String",
  "tenantIds": "String",
  "tenantNames": "String"
}
```
