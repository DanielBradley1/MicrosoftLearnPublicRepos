<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageaccessentity -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# packageAccessEntity complex type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents an access entity \(user or group\) with permissions to access a Copilot package.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| `resourceId` | String | Unique identifier of the user or group. |
| `resourceType` | [accessEntityType](#accessentitytype-enumeration) | Type of entity. |

### accessEntityType enumeration

| Value | Description |
| :--- | :--- |
| `user` | User entity. |
| `group` | Group entity. |
| `unknownFutureValue` | [Evolvable sentinel value](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.packageAccessEntity",
  "resourceId": "String",
  "resourceType": "String"
}
```
