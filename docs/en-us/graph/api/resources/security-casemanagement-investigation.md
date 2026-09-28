<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-investigation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# investigation resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains investigation details for an [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta). Returned in the **investigation** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int32 | The number of investigations. |
| ids | String collection | The investigation identifiers. |
| state | String | The investigation state. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.investigation",
  "ids": [
    "String"
  ],
  "count": "Integer",
  "state": "String"
}
```
