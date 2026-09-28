<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-recommendationrelation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# recommendationRelation resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a relation between a case and a recommendation.

For cast segments in URLs, use the full type name, for example `microsoft.graph.security.caseManagement.recommendationRelation`.

Inherited from [relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [relation resource](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

To use a supported query option with a property declared only on **recommendationRelation**, cast the base relations collection to `microsoft.graph.security.caseManagement.recommendationRelation`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| recommendationType | String | The recommendation type associated with the linked recommendation. |
| relatedResourceId | String | The identifier of the related recommendation. Inherited from [relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta). |
| resourceGroupName | String | The Azure resource group name for the related recommendation. |
| subscriptionId | String | The Azure subscription identifier for the related recommendation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.recommendationRelation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "relatedResourceId": "String",
  "recommendationType": "String",
  "subscriptionId": "String",
  "resourceGroupName": "String"
}
```
