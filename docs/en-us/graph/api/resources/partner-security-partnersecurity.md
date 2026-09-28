<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# partnerSecurity resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the root for partner security entities.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| securityAlerts | [microsoft.graph.partner.security.partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) collection | The security alerts or a vulnerability of a Cloud Solution Provider \(CSP\) partner's customer that the partner must be made aware of for further action. |
| securityScore | [microsoft.graph.partner.security.securityScore](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityscore?view=graph-rest-beta) singleton | The security score calculated for the CSP partner and their customers. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.partnerSecurity"
}
```
