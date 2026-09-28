<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emailsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# emailSettings resource type

Namespace: microsoft.graph

Defines the settings for emails sent from Lifecycle Workflows tasks. This object is configured in the **emailSettings** property of the [lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) resource. It allows you to use a verified custom [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) and [organizationalBranding](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding?view=graph-rest-1.0) with emails sent out via workflow tasks.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| senderDomain | String | Specifies the [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) that should be used when sending email notifications. This domain must be [verified](https://learn.microsoft.com/en-us/graph/api/domain-verify?view=graph-rest-1.0) in order to be used. We recommend that you use a domain that has the appropriate DNS records to facilitate email validation, like SPF, DKIM, DMARC, and MX, because this then complies with the [RFC compliance](https://www.ietf.org/rfc/rfc2142.txt) for sending and receiving email. For details, see [Learn more about Exchange Online Email Routing](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/mail-flow-best-practices). |
| useCompanyBranding | Boolean | Specifies if the organization’s banner logo should be included in email notifications. The banner logo will replace the Microsoft logo at the top of the email notification. If `true` the banner logo will be taken from the tenant’s [branding settings](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding?view=graph-rest-1.0). This value can only be set to `true` if the [organizationalBranding](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding?view=graph-rest-1.0) **bannerLogo** property is set. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emailSettings",
  "senderDomain": "String",
  "useCompanyBranding": "Boolean"
}
```
