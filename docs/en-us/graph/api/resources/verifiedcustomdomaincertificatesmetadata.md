<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiedcustomdomaincertificatesmetadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# verifiedCustomDomainCertificatesMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the custom domain certificate metadata \(**verifiedCustomDomainCertificatesMetadata** property\) for the [onPremisesPublishing](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishing?view=graph-rest-beta) resource when publishing an on-premises application with Application Proxy. Using a custom domain allows you to use your own domain name instead of the default domain, msappproxy.net, for your application. To learn more see, [Custom domains in Microsoft Entra application proxy](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-configure-custom-domain).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expiryDate | DateTimeOffset | The expiry date of the custom domain certificate. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| issueDate | DateTimeOffset | The issue date of the custom domain. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| issuerName | String | The issuer name of the custom domain certificate. |
| subjectName | String | The subject name of the custom domain certificate. |
| thumbprint | String | The thumbprint associated with the custom domain certificate. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "expiryDate": "String (timestamp)",
  "issueDate": "String (timestamp)",
  "issuerName": "String",
  "subjectName": "String",
  "thumbprint": "String"
}
```
