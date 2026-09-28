<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentrelation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# incidentRelation resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a relation between a case and an incident. Creating an **incidentRelation** for an [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) isn't supported.

For cast segments in URLs, use the full type name, for example `microsoft.graph.security.caseManagement.incidentRelation`.

Inherited from [relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [relation resource](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| relatedResourceId | String | The identifier of the related external resource. Inherited from [relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.incidentRelation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "relatedResourceId": "String"
}
```
