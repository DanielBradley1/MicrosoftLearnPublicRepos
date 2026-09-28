<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/report-identity-access?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Identity and access reports API overview

With Microsoft Graph, you can programmatically access identity and access reports to monitor and troubleshoot all activities in your tenant. In addition, you can analyze these logs with Azure Monitor logs and Log Analytics, or stream to third-party SIEM tools for further investigations.

The availability of all Microsoft Entra identity and access reports is governed by the [Microsoft Entra data retention policies](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/reference-reports-data-retention#how-long-does-azure-ad-store-the-data).

For more information about identity and access reports, see [Microsoft Entra monitoring and health](https://learn.microsoft.com/en-us/entra/identity/monitoring-health) and [Microsoft Entra monitoring and health licensing information](https://learn.microsoft.com/en-us/entra/fundamentals/licensing#microsoft-entra-monitoring-and-health).

## Available reports

### Application activity reports

#### AD FS application activity

The AD FS application activity report provides information about how a relying party is configured with Active Directory Federation Services \(AD FS\), its aggregated usage, and whether the relying party configuration can be migrated to Microsoft Entra ID. For more information, see the [relyingPartyDetailedSummary](https://learn.microsoft.com/en-us/graph/api/resources/applicationsigninsummary) resource.

#### Authentication methods registration and usage activity

Authentication methods activity reports provide information on the registration and usage of [authentication methods](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview?view=graph-rest-1.0) in your tenant. For example, how many users are registered for an authentication method, how any are capable for MFA or SSPR, and so on. You can determine which authentication methods are more successful for your organization, what types of errors end users are running into, and what campaign you need to run to help your end users adopt the use of SSPR and MFA.

For more information, see [authentication method usage APIs](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-usage-insights-overview?view=graph-rest-1.0).

### Microsoft Entra audit logs

Audit logs are available for sign-ins, activities in the directory, and provisioning. For more information, see [Microsoft Entra audit logs](https://learn.microsoft.com/en-us/graph/api/resources/azure-ad-auditlog-overview?view=graph-rest-1.0).

## Reports in preview only

The following reports are available on the `beta` endpoint only:

- [Application credential sign-in activity](https://learn.microsoft.com/en-us/graph/api/resources/appcredentialsigninactivity?view=graph-rest-beta&preserve-view=true)
- [Service principal sign-in activity](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsigninactivity?view=graph-rest-beta&preserve-view=true)
- Application sign-in reports: [summarized count](https://learn.microsoft.com/en-us/graph/api/resources/applicationsigninsummary?view=graph-rest-beta&preserve-view=true) or [detailed report](https://learn.microsoft.com/en-us/graph/api/resources/applicationsignindetailedsummary?view=graph-rest-beta&preserve-view=true)
- Application user activity for Microsoft Entra External ID: [daily insights](https://learn.microsoft.com/en-us/graph/api/resources/dailyuserinsightmetricsroot?view=graph-rest-beta&preserve-view=true) and [monthly insights](https://learn.microsoft.com/en-us/graph/api/resources/monthlyuserinsightmetricsroot?view=graph-rest-beta&preserve-view=true)
- Health reports: [SLA attainment](https://learn.microsoft.com/en-us/graph/api/azureadauthentication-get?view=graph-rest-beta&preserve-view=true), [service activity](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta&preserve-view=true), and [health monitoring](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-overview?view=graph-rest-beta&preserve-view=true)
- The following authentication methods registration and usage reports

  - [Credential usage summary](https://learn.microsoft.com/en-us/graph/api/resources/credentialusagesummary?view=graph-rest-beta&preserve-view=true)
  - [Credential user registration count](https://learn.microsoft.com/en-us/graph/api/resources/credentialuserregistrationcount?view=graph-rest-beta&preserve-view=true)
  - [User credential usage details](https://learn.microsoft.com/en-us/graph/api/resources/usercredentialusagedetails?view=graph-rest-beta&preserve-view=true)

- [Microsoft Entra recommendations](https://learn.microsoft.com/en-us/graph/api/resources/recommendations-api-overview?view=graph-rest-beta&preserve-view=true)

## Related content

- For more information about these reports, see [Microsoft Entra monitoring and health](https://learn.microsoft.com/en-us/entra/identity/monitoring-health)
