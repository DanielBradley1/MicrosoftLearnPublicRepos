<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlstermination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-10 -->

# tlsTermination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A container for tenant-level TLS inspection settings for Global Secure Access.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| externalCertificateAuthorityCertificates | [microsoft.graph.networkaccess.externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) collection | List of customer's Certificate Authority \(CA\) certificates used for TLS inspection in Global Secure Access |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsTermination"
}
```
