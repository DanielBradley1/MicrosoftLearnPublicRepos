<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-accountentitymapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# accountEntityMapping resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) query result to an account entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aadUserIdColumn | String | Name of the detection query column that maps to the Microsoft Entra user ID of the alert entity. |
| dnsDomainColumn | String | Name of the detection query column that maps to the DNS domain of the alert entity. |
| nameColumn | String | Name of the detection query column that maps to the name of the alert entity. |
| ntDomainColumn | String | Name of the detection query column that maps to the NT domain of the alert entity. |
| sidColumn | String | Name of the detection query column that maps to the security identifier \(SID\) of the alert entity. |
| upnColumn | String | Name of the detection query column that maps to the user principal name \(UPN\) of the alert entity. |
| upnSuffixColumn | String | Name of the detection query column that maps to the UPN suffix of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.accountEntityMapping",
  "aadUserIdColumn": "String",
  "dnsDomainColumn": "String",
  "nameColumn": "String",
  "ntDomainColumn": "String",
  "sidColumn": "String",
  "upnColumn": "String",
  "upnSuffixColumn": "String"
}
```
