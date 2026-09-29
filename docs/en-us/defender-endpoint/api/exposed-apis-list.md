<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-list -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Supported Microsoft Defender for Endpoint APIs

Important

Advanced hunting capabilities are not included in Defender for Business.

## Endpoint URI and versioning

### Endpoint URI

> The service base URI is: [https://api.security.microsoft.com](https://api.security.microsoft.com)
> 
> The queries based OData have the '/api' prefix. For example, to get Alerts you can send GET request to [https://api.security.microsoft.com/api/alerts](https://api.security.microsoft.com/api/alerts)

### Versioning

> The API supports versioning.
> 
> > The current version is **V1.0**. To use a specific version, use this format: `https://api.security.microsoft.com/api/{Version}`. For example: `https://api.security.microsoft.com/api/v1.0/alerts`
> 
> If you don't specify any version \(e.g. `https://api.security.microsoft.com/api/alerts`\) you will get to the latest version.

Note

If you're a US Government customer, use the URIs listed in [Microsoft Defender for Endpoint for US Government customers](https://learn.microsoft.com/en-us/defender-endpoint/gov#api).

Tip

For better performance, instead of using api.security.microsoft.com, use a server closer to your geolocation:

- us.api.security.microsoft.com
- eu.api.security.microsoft.com
- uk.api.security.microsoft.com
- au.api.security.microsoft.com
- swa.api.security.microsoft.com
- ina.api.security.microsoft.com
- aea.api.security.microsoft.com

Learn more about the individual supported entities where you can run API calls to and details such as HTTP request values, request headers and expected responses.

## In this section

| Topic | Description |
| --- | --- |
| [**Advanced Hunting** methods](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-api) | Run queries from API. |
| [**Alert** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) | Run API calls such as - get alerts, create alert, update alert and more. |
| [Export **Assessment** per-device methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/get-assessment-methods-properties) | Run API calls to gather vulnerability assessments on a per-device basis, such as: - export secure configuration assessment, export software inventory assessment, export software vulnerabilities assessment, and delta export software vulnerabilities assessment. |
| [**Automated investigation** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/investigation) | Run API calls such as - get collection of Investigation. |
| [Export device health methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/device-health-api-methods-properties) | Run API Calls such as - GET /api/public/avdeviceshealth. |
| [**Domain**-related alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/get-domain-related-alerts) | Run API calls such as - get domain-related devices, domain statistics and more. |
| [**File** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/files) | Run API calls such as - get file information, file related alerts, file related devices, and file statistics. |
| [**Indicators** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator) | Run API call such as - get Indicators, create Indicator, and delete Indicators. |
| [**IP**-related alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/get-ip-related-alerts) | Run API calls such as - get IP-related alerts and get IP statistics. |
| [**Machine** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) | Run API calls such as - get devices, get devices by ID, information about logged on users, edit tags and more. |
| [**Machine Action** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/machineaction) | Run API call such as - Isolation, Run anti-virus scan and more. |
| [**Recommendation** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/recommendation) | Run API calls such as - get recommendation by ID. |
| [**Remediation activity** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/get-remediation-methods-properties) | Run API call such as - get all remediation tasks, get exposed devices remediation task and get one remediation task by id. |
| [**Score** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/score) | Run API calls such as - get exposure score or get device secure score. |
| [**Software** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/software) | Run API calls such as - list vulnerabilities by software. |
| [**User** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/user) | Run API calls such as - get user-related alerts and user-related devices. |
| [**Vulnerability** methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/vulnerability) | Run API calls such as - list devices by vulnerability. |

## See also

- [Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)
- [Microsoft Defender for Endpoint API release notes](https://learn.microsoft.com/en-us/defender-endpoint/api/api-release-notes)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
