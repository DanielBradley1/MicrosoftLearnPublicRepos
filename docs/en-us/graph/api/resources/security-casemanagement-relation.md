<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# relation resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a link from a case to another security resource. This abstract type can't be instantiated directly. Use one of the following concrete derived types, identified by `@odata.type`:

- [incidentRelation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentrelation?view=graph-rest-beta)
- [recommendationRelation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-recommendationrelation?view=graph-rest-beta)
- [workspaceIndicatorRelation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-workspaceindicatorrelation?view=graph-rest-beta)

Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-list-relations?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta) collection | List external resource relations for a case. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-post-relations?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta) | Create a relation from a case to another security resource. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-relation-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta) | Read a concrete relation from a case. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-relation-update?view=graph-rest-beta) | None | Update the properties of a relation object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-relation-delete?view=graph-rest-beta) | None | Delete a relation from a case. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| relatedResourceId | String | The identifier of the related external resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.relation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "relatedResourceId": "String"
}
```
