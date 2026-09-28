<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activityresourcedetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# activityResourceDetails resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains details about the resource associated with an [auditLog](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-auditlog?view=graph-rest-beta). Returned in the **details** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kind | String | The resource kind, such as task or relation. |
| resourceId | String | The identifier of the resource associated with the activity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.activityResourceDetails",
  "resourceId": "String",
  "kind": "String"
}
```
