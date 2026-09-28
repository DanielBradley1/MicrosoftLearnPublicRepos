<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-validitydate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# validityDate resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

"Represents the validity dates for an [externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) "

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | Date and time when certificate validity expires. |
| startDateTime | DateTimeOffset | Date and time when certificate validity begins. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.validityDate",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)"
}
```
