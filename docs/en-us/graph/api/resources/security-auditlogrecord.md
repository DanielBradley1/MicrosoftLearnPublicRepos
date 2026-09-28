<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# auditLogRecord resource type

Namespace: microsoft.graph.security

Represents an individual audit log record from the Microsoft 365 unified audit log. Each record captures a specific activity or event across Microsoft 365 services.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-auditlogquery-list-records?view=graph-rest-1.0) | [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0) collection | Get a list of the [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| administrativeUnits | String collection | The collection of administrative units associated with the record. |
| auditData | [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0) | The audit data associated with the record. |
| auditLogRecordType | [microsoft.graph.security.auditLogRecordType](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecordtype?view=graph-rest-1.0) | The type of the audit log record. |
| clientIp | String | The IP address of the client that performed the activity. |
| createdDateTime | DateTimeOffset | The date and time when the activity was performed. |
| id | String | The unique identifier for the audit log record. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| objectId | String | The identifier of the object that was affected by the activity. |
| operation | String | The name of the activity that was performed. |
| organizationId | String | The GUID of the organization's Microsoft 365 tenant. |
| service | String | The Microsoft 365 service where the activity occurred. |
| userId | String | The identifier of the user, system account, service, or application that performed the activity. |
| userPrincipalName | String | The user principal name of the user who performed the activity. |
| userType | microsoft.graph.security.auditLogUserType | The type of user who performed the activity. Possible values are: `regular`, `reserved`, `admin`, `dcAdmin`, `system`, `application`, `servicePrincipal`, `customPolicy`, `systemPolicy`, `partnerTechnician`, `guest`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.auditLogRecord",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "auditLogRecordType": "String",
  "operation": "String",
  "organizationId": "String",
  "userType": "String",
  "userId": "String",
  "service": "String",
  "objectId": "String",
  "userPrincipalName": "String",
  "clientIp": "String",
  "administrativeUnits": ["String"],
  "auditData": {"@odata.type": "microsoft.graph.security.auditData"}
}
```
