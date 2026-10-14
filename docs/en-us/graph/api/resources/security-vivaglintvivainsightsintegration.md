<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-vivaglintvivainsightsintegration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# vivaGlintVivaInsightsIntegration resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Audit data for Viva Glint Viva Insights Integration events returned in the **auditData** property of an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta).

This resource is an open type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dynamicProperties | [microsoft.graph.security.auditRecordTypeDictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-auditrecordtypedictionary?view=graph-rest-beta) | An open-type dictionary that contains dynamic audit event properties as name-value pairs. Inherited from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.vivaGlintVivaInsightsIntegration",
  "dynamicProperties": {
    "@odata.type": "microsoft.graph.security.auditRecordTypeDictionary"
  }
}
```
