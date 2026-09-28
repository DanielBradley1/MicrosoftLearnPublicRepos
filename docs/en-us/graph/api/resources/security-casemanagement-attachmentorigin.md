<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachmentorigin?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# attachmentOrigin resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains information about the resource from which an [attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) originated. Returned in the **origin** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceId | String | The identifier of the origin resource. |
| resourceType | [microsoft.graph.security.caseManagement.attachmentOriginType](#attachmentorigintype-values) | The type of origin resource. |

### attachmentOriginType values

| Member | Description |
| :--- | :--- |
| case | The attachment originated from a case. |
| comment | The attachment originated from a comment activity. |
| task | The attachment originated from a task. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.attachmentOrigin",
  "resourceId": "String",
  "resourceType": "String"
}
```
