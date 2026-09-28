<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseducertificatesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosEduCertificateSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Trusted Root and PFX certificates for iOS EDU.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| trustedRootCertificate | Binary | Trusted Root Certificate. |
| certFileName | String | File name to display in UI. |
| certificationAuthority | String | PKCS Certification Authority. |
| certificationAuthorityName | String | PKCS Certification Authority Name. |
| certificateTemplateName | String | PKCS Certificate Template Name. |
| renewalThresholdPercentage | Int32 | Certificate renewal threshold percentage. Valid values 1 to 99 |
| certificateValidityPeriodValue | Int32 | Value for the Certificate Validity Period. |
| certificateValidityPeriodScale | [certificateValidityPeriodScale](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatevalidityperiodscale?view=graph-rest-beta) | Scale for the Certificate Validity Period. Possible values are: `days`, `months`, `years`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosEduCertificateSettings",
  "trustedRootCertificate": "binary",
  "certFileName": "String",
  "certificationAuthority": "String",
  "certificationAuthorityName": "String",
  "certificateTemplateName": "String",
  "renewalThresholdPercentage": 1024,
  "certificateValidityPeriodValue": 1024,
  "certificateValidityPeriodScale": "String"
}
```
