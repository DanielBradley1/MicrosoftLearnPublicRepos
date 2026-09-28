<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# caseTypeConfiguration resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Exposes the discovery configuration for a single case type: the allowed status tree and the custom-field schema \(the blank-form definition\) that applies to every [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) of that type.

Each configuration is keyed by **id**, whose value is the case type: `genericCase`, `incidentCase`, or `exposureCase`. The configuration is reached by containment navigation from the case management root at `/security/caseManagement/caseTypeConfigurations`, so each contained status and custom field is individually addressable. The collection and all of its contained resources are read-only.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagementroot-list-casetypeconfigurations?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta) collection | Get a list of the [caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta) object. |
| [List customFields](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-customfields?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta) collection | Get the custom-field definitions that make up the blank-form schema for this case type. |
| [List statuses](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-statuses?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.statusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta) collection | Get the top-level statuses that make up the allowed status tree for this case type. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultStatusId | String | The **id** of the top-level [status](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta) that a new case of this type starts in. |
| displayName | String | The human-readable label of the case type. |
| id | String | The unique identifier of the case type. The value is the case type name: `genericCase`, `incidentCase`, or `exposureCase`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customFields | [microsoft.graph.security.caseManagement.customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta) collection | The contained custom-field definitions that make up the blank-form schema for this case type. Read-only. Supports `$count`, `$expand`, `$filter`, `$orderby`, `$select`, `$skip`, and `$top`. |
| statuses | [microsoft.graph.security.caseManagement.statusDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-statusdefinition?view=graph-rest-beta) collection | The contained top-level statuses that a case of this type can be set to. Read-only. Supports `$count`, `$expand`, `$filter`, `$orderby`, `$select`, `$skip`, and `$top`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.caseTypeConfiguration",
  "id": "String (identifier)",
  "displayName": "String",
  "defaultStatusId": "String"
}
```
