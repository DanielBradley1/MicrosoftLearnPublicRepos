<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantdatasecurityandgovernance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-04 -->

# tenantDataSecurityAndGovernance resource type

Namespace: microsoft.graph

Represents the entry point for data security and governance features applicable across the entire tenant.

Inherits from [dataSecurityAndGovernance](https://learn.microsoft.com/en-us/graph/api/resources/datasecurityandgovernance?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Process content async](https://learn.microsoft.com/en-us/graph/api/tenantdatasecurityandgovernance-processcontentasync?view=graph-rest-1.0) | [processContentResponses](https://learn.microsoft.com/en-us/graph/api/resources/processcontentresponses?view=graph-rest-1.0) collection | Process a batch of content entries asynchronously against data protection policies. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique ID of the data security and governance stream. Inherited from [dataSecurityAndGovernance](https://learn.microsoft.com/en-us/graph/api/resources/datasecurityandgovernance?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| protectionScopes | [tenantProtectionScopeContainer](https://learn.microsoft.com/en-us/graph/api/resources/tenantprotectionscopecontainer?view=graph-rest-1.0) | Container for actions related to computing tenant-wide data protection scopes. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantDataSecurityAndGovernance",
  "id": "String (identifier)"
}
```
