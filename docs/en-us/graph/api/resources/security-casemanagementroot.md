<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagementroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# caseManagementRoot resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the entry point for Microsoft Graph security case management APIs. Use this resource to access cases that organize security investigations, related work, activities, and evidence.

| Context | Example |
| :--- | :--- |
| URL cast segment | `.../cases/microsoft.graph.security.caseManagement.incidentCase` |
| JSON body discriminator | `"@odata.type": "#microsoft.graph.security.caseManagement.incidentCase"` |

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| caseTypeConfigurations | [microsoft.graph.security.caseManagement.caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta) collection | The collection of case type configurations that define the statuses and custom fields available for each case type. Read-only. Supports `$select`, `$count`, and `$expand` of the `statuses` and `customFields` relationships. |
| cases | [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) collection | The collection of security cases managed through the case management entry point. Supports `$filter`, `$orderby`, `$select`, `$top`, and `$skip`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagementRoot"
}
```
