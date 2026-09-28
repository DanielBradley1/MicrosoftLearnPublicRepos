<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# zone resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an aggregate of cloud-native environments \(also referred to as a *cloud scope*\) used to manage access and security at scale within Microsoft Defender for Cloud. Zones enable the segmentation of multi-cloud environments, such as Azure, AWS, GCP, and connected DevOps or registry sources, into meaningful groupings, allowing for the consistent application of least‑privilege access controls.

When you set up a new zone, you can assign roles to it. For more information about role‑based access control permission assignments, see [rbacApplicationMultiple](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplicationmultiple?view=graph-rest-beta).

For more information, see [Manage cloud scopes and unified role-based access control](https://learn.microsoft.com/en-us/azure/defender-for-cloud/cloud-scopes-unified-rbac?pivots=defender-portal).

Note

A tenant has no default zone. Environments aren't automatically attached to any zone; they must be explicitly assigned to zones by administrators. An environment can be attached to multiple zones simultaneously, which allows for flexible grouping and overlapping access‑control scenarios.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-security-list-zones?view=graph-rest-beta) | [microsoft.graph.security.zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) collection | Get a list of the [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-security-post-zones?view=graph-rest-beta) | [microsoft.graph.security.zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) | Create a new [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-zone-get?view=graph-rest-beta) | [microsoft.graph.security.zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) | Get a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object by a specific **zoneId**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-zone-update?view=graph-rest-beta) | [microsoft.graph.security.zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) | Update the properties of a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-zone-delete?view=graph-rest-beta) | None | Delete a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object by providing the **zoneId**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| created | [microsoft.graph.security.auditInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-auditinfo?view=graph-rest-beta) | Creation metadata, including user and timestamp. Supports `$orderby` \(**dateTime** property only\). Supports `$filter` \(`ge`, `le`, `gt`, `lt`\) on the **dateTime** property. For example, `$filter=created/dateTime ge 2023-01-01T00:00:00Z`. |
| description | String | Optional description of the zone. Up to 255 characters. Supports `$filter` \(`eq`, `contains`\). For example, `$filter=contains(description, 'production')`. |
| displayName | String | Human-readable name of the zone. Up to 1,024 characters. Supports `$filter` \(`eq`, `contains`\), and `$orderby`. For example, `$filter=displayName eq 'Production Zone'` or `$orderby=displayName asc`. |
| id | String | Unique identifier for the zone. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`\). |
| modified | [microsoft.graph.security.auditInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-auditinfo?view=graph-rest-beta) | Last modification metadata, including user and timestamp. Supports `$orderby` \(**dateTime** property only\). Supports `$filter` \(`ge`, `le`, `gt`, `lt`\) on the **dateTime** property. For example, `$orderby=modified/dateTime desc`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| aggregations | [microsoft.graph.security.aggregatedEnvironment](https://learn.microsoft.com/en-us/graph/api/resources/security-aggregatedenvironment?view=graph-rest-beta) collection | Environment count summaries by type. Read-only. Supports `$filter` \(`eq`\) on the **kind** property. For example, `$filter=aggregations/any(a: a/kind eq 'azureSubscription')`. |
| environments | [microsoft.graph.security.environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) collection | Collection of attached environments. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.zone",
  "created": {"@odata.type": "microsoft.graph.security.auditInfo"},
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "modified": {"@odata.type": "microsoft.graph.security.auditInfo"}
}
```
