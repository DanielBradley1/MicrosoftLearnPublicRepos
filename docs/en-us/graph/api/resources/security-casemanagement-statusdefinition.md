<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# statusDefinition resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a top-level status that a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) of a given type can be set to. A **statusDefinition** belongs to the allowed status tree of a [caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta) and carries a nested collection of custom statuses that are returned inline.

Status definitions are reached by containment navigation from a case type configuration at `/security/caseManagement/caseTypeConfigurations/{caseTypeConfigurationId}/statuses`, so each status is individually addressable. The collection is read-only. Custom statuses are returned inline as [customStatusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customstatusdefinition?view=graph-rest-beta) values within the **customStatuses** property and aren't separately addressable.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-statuses?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.statusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta) collection | Get a list of the [statusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta) objects for a case type. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-statusdefinition-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.statusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta) | Read the properties of a [statusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customStatuses | [microsoft.graph.security.caseManagement.customStatusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customstatusdefinition?view=graph-rest-beta) collection | The custom statuses returned inline within this top-level status. These aren't separately addressable. |
| displayName | String | The human-readable label of the status. Supports `$filter` and `$orderby`. |
| id | String | The unique identifier of the status within the case type. Read-only. Supports `$filter` and `$orderby`. |
| sortOrder | Int32 | The display order of the status relative to other statuses of the same case type. Supports `$filter` and `$orderby`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.statusDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "sortOrder": "Int32",
  "customStatuses": [
    {
      "@odata.type": "microsoft.graph.security.caseManagement.customStatusDefinition",
      "customStatusId": "String",
      "displayName": "String",
      "sortOrder": "Int32",
      "isFinal": "Boolean"
    }
  ]
}
```
