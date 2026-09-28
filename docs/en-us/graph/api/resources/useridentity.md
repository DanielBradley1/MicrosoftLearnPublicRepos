<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# userIdentity resource type

Namespace: microsoft.graph

In the context of a Microsoft Entra audit log, this resource represents the user information that initiated or was affected by an audit activity.

- In the context of [callRecords](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0), this resource represents the identity of a [participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) or [organizer](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-organizer?view=graph-rest-1.0) in a call.
- It's also returned in the **user** property of [auditActivityInitiator](https://learn.microsoft.com/en-us/graph/api/resources/auditactivityinitiator?view=graph-rest-1.0).

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity. This might not always be available or up-to-date. |
| id | String | Unique identifier for the identity. Nullable. When the unique identifier is unavailable, the **displayName** property is provided for the identity, but the **id** property isn't included in the response. |
| ipAddress | String | Indicates the client IP address associated with the user performing the activity \(audit log only\). |
| userPrincipalName | String | The **userPrincipalName** attribute of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)",
  "ipAddress": "String",
  "userPrincipalName": "String"
}
```
