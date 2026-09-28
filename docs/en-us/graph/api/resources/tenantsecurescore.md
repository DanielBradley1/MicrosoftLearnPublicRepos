<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantsecurescore?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# tenantSecureScore resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Secure Score for a Microsoft Entra tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createDateTime | DateTimeOffset | When this Secure Score was created. |
| tenantMaxScore | Int64 | The maximum historical Secure Score for the tenant. |
| tenantScore | Int64 | The Secure Score. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantSecureScore",
  "tenantScore": "Integer",
  "tenantMaxScore": "Integer",
  "createDateTime": "String (timestamp)"
}
```
