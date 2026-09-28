<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# Use the Microsoft Graph security API

The Microsoft Graph security API provides a unified interface and schema to integrate with security solutions from Microsoft and ecosystem partners. This empowers customers to streamline security operations and better defend against increasing cyber threats. The Microsoft Graph security API federates queries to all onboarded security providers and aggregates responses. Use the Microsoft Graph security API to build applications that:

- Consolidate and correlate security alerts from multiple sources.
- Pull and investigate all incidents and alerts from services that are part of or integrated with Microsoft 365 Defender.
- Unlock contextual data to inform investigations.
- Automate security tasks, business processes, workflows, and reporting.
- Send threat indicators to Microsoft products for customized detections.
- Invoke actions to in response to new threats.
- Provide visibility into security data to enable proactive risk management.

The Microsoft Graph security API provides key features as described in the following sections.

## Advanced hunting

Advanced hunting is a query-based threat-hunting tool that lets you explore up to 30 days of raw data. You can proactively inspect events in your network to locate threat indicators and entities. The flexible access to data enables unconstrained hunting for both known and potential threats.

Use [runHuntingQuery](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0) to run a [Kusto Query Language](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/) \(KQL\) query on data stored in Microsoft 365 Defender. Use the returned result set to enrich an existing investigation or to uncover undetected threats in your network.

### Quotas and resource allocation

The following conditions relate to all queries.

1. Queries explore and return data from the past 30 days.
2. Results can return up to 100,000 rows.
3. You can make up to at least 45 calls per minute per tenant. The number of calls varies per tenant based on its size.
4. Each tenant is allocated CPU resources, based on the tenant size. Queries are blocked if the tenant reaches 100% of the allocated resources until after the next 15-minute cycle. To avoid blocked queries due to excess consumption, follow the guidance in [Optimize your queries to avoid hitting CPU quotas](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-best-practices).
5. If a single request runs for more than three minutes, it times out and returns an error.
6. A `429` HTTP response code indicates that you reached the allocated CPU resources, either by the number of requests sent or by allotted running time. Read the response body to understand the limit you reached.
7. Query results have an overall size limit of 50 MB. This limit doesn't just refer to the number of records; factors such as the number of columns, data types, and field lengths also contribute to the query result size.

### Migrate from the older APIs

The advanced hunting APIs in Microsoft Graph replace the older version of the API that was available through the `https://api.security.microsoft.com/api/advancedhunting/run` and `https://api.security.microsoft.com/api/advancedqueries/run` endpoints. The older APIs are now retired and will stop returning data on February 1, 2027.

To migrate to the advanced hunting APIs in Microsoft Graph, update the following parameters in your application:

| Subject | Older parameters | Microsoft Graph |
| --- | --- | --- |
| Endpoints | [https://api.securitycenter.microsoft.com/api/advancedqueries/run](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-api)  <br>  <br>[https://api.security.microsoft.com/api/advancedhunting/run](https://learn.microsoft.com/en-us/defender-xdr/api-advanced-hunting) | [https://graph.microsoft.com/beta/security/runHuntingQuery](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0) |
| Resource URI | Microsoft Defender for Endpoint on `https://api.securitycenter.microsoft.com` | Microsoft Graph on `https://graph.microsoft.com` |
| API permissions | *AdvancedQuery.Read* \(delegated\) and *AdvancedQuery.Read.All* \(application\) under Microsoft Defender for Endpoint \(formerly Windows Defender Advanced Threat Protection\)  <br>  <br>*AdvancedHunting.Read* \(delegated\) and *AdvancedHunting.Read.All* \(application\) under Microsoft Threat Protection | [*ThreatHunting.Read.All*](https://learn.microsoft.com/en-us/graph/permissions-reference#threathuntingreadall) \(delegated and application\) |
| Request body | **Query** property. For example `{"Query":"DeviceProcessEvents \|where InitiatingProcessFileName =~ 'powershell.exe' \|where ProcessCommandLine contains 'appdata'\|project Timestamp, FileName, InitiatingProcessFileName, DeviceId\|limit 2"}` | **Query** and **Timespan** properties. For example, `{"Query": "DeviceProcessEvents", "Timespan": "P90D"}` |
| Response | **QueryResponse** object consisting of **Stats**, **Schema**, and **Results** | [huntingQueryResults resource type](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingqueryresults?view=graph-rest-1.0)", consisting of **schema** \(instead of **Schema**\) and **results** \(instead of **Results**\). |

For more information about how to authorize your app to call Microsoft Graph APIs, see [Get access on behalf of a user](https://learn.microsoft.com/en-us/graph/auth-v2-user) and [Get access without a user](https://learn.microsoft.com/en-us/graph/auth-v2-service).

#### Power Platform flow migration \(PowerApps / Power Automate / Logic Apps\)

Microsoft Graph does't have a built-in Advanced Hunting action that was available in the Power Platform connector for Microsoft Defender ATP. To continue using Advanced Hunting in your Power Platform flows, create a custom connector. For more information, see [Create a Microsoft Graph JSON Batch Custom Connector for Power Automate](https://learn.microsoft.com/en-us/graph/tutorials/power-automate) and use the Microsoft Graph parameters described in the preceding table.

#### Power BI flow migration

If you're using a custom Power BI report created with the older API, update your Power BI query to use the Microsoft Graph parameters described in the preceding table. For more information, see [Create custom Microsoft Defender XDR reports using Microsoft Graph security API and Power BI](https://learn.microsoft.com/en-us/defender-xdr/defender-xdr-custom-reports).

## Alerts

Alerts are detailed warnings about suspicious activities in a customer's tenant that Microsoft or partner security providers identified and flagged for action. Attacks typically employ various techniques against different types of entities, such as devices, users, and mailboxes. The result is alerts from multiple security providers for multiple entities in the tenant. Piecing the individual alerts together to gain insight into an attack can be challenging and time-consuming.

The security API offers two types of alerts that aggregate other alerts from security providers and make analyzing attacks and determining responses easier:

- [Alerts and incidents](#alerts-and-incidents) - these are the latest generation of alerts in the Microsoft Graph security API. They're represented by the [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) resource and its collection, [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) resource, defined in the `microsoft.graph.security` namespace.
- [Legacy alerts](#legacy-alerts) - these are the first generation of alerts in the Microsoft Graph security AI. They're represented by the [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) resource defined in the `microsoft.graph` namespace.

Important

To view Sentinel alerts and incidents you must onboard Sentinel to the Defender Portal. For more information see [Connect Microsoft Sentinel to the Microsoft Defender portal](https://learn.microsoft.com/en-us/unified-secops/microsoft-sentinel-onboard).

### Alerts and incidents

These [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) resources first pull alert data from security provider services, that are either part of or integrated with [Microsoft 365 Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-defender?view=o365-worldwide&preserve-view=true). Then they consume the data to return rich, valuable clues about a completed or ongoing attack, the impacted assets, and associated [evidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). In addition, they automatically correlate other alerts with the same attack techniques or the same attacker into an [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) to provide a broader context of an attack. They recommend response and remediation actions, offering consistent actionability across all the different providers. The rich content makes it easier for analysts to collectively investigate and respond to threats.

Alerts from the following security providers are available via these rich alerts and incidents:

- [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection)
- [Microsoft 365 Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-defender?view=o365-worldwide&preserve-view=true)
- [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/monitor-alerts)
- [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint?view=o365-worldwide&preserve-view=true)
- [Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/alerts-overview)
- [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/overview?view=o365-worldwide&preserve-view=true)
- [Microsoft Purview Data Loss Prevention](https://learn.microsoft.com/en-us/microsoft-365/compliance/dlp-learn-about-dlp?view=o365-worldwide&preserve-view=true)
- [Microsoft Purview Insider Risk Management](https://learn.microsoft.com/en-us/purview/insider-risk-management?view=o365-worldwide&preserve-view=true)

### Legacy alerts

Important

The legacy alerts API is deprecated and will be retired on October 15, 2026. Migrate to the new [alerts and incidents](https://learn.microsoft.com/en-us/graph/api/resources/security-alert) API. For more information, see [Migrate from legacy alerts to the alerts and incidents API](https://learn.microsoft.com/en-us/graph/alertsv1-alertsv2-migration).

The legacy [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) resources federate calling of supported Azure and Microsoft 365 Defender security providers. They aggregate common alert data among the different domains to allow applications to unify and streamline management of security issues across all integrated solutions. They enable applications to correlate alerts and context to improve threat protection and response.

The legacy version of the security API offers the [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) resource that federates calling of supported Azure and Microsoft 365 Defender security providers. This **alert** resource aggregates alert data that's common among the different domains to allow applications to unify and streamline management of security issues across all integrated solutions. This enables applications to correlate alerts and context to improve threat protection and response.

With the alert update capability, you can sync the status of specific alerts across different security products and services that are integrated with the Microsoft Graph security API by updating your **alert** entity.

Alerts from the following providers are available via the **alert** resource. Support for GET alerts, PATCH alerts, and subscribe \(via webhooks\) is indicated in the following table.

| Security provider | GET alert | PATCH alert | Subscribe to alert |
| :--- | :--- | :--- | :--- |
| [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/playbook) | ✓ | [File issue](https://github.com/microsoftgraph/security-api-solutions/issues/new) \* | ✓ |
| Microsoft 365<br><br>- [Default](https://learn.microsoft.com/en-us/office365/securitycompliance/alert-policies#default-alert-policies)<br>- [Cloud App Security](https://learn.microsoft.com/en-us/office365/securitycompliance/anomaly-detection-policies-in-ocas)<br>- Custom Alert | ✓ | [File issue](https://github.com/microsoftgraph/security-api-solutions/issues/new) | [File issue](https://github.com/microsoftgraph/security-api-solutions/issues/new) |
| [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/monitor-alerts) | ✓ | [File issue](https://github.com/microsoftgraph/security-api-solutions/issues/new) \* | ✓ |
| [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-simulations) \*\* | ✓ | ✓ | [File issue](https://github.com/microsoftgraph/security-api-solutions/issues/new) |
| [Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/understanding-security-alerts#security-alert-categories) \*\*\* | ✓ | [File issue](https://github.com/microsoftgraph/security-api-solutions/issues/new) \* | ✓ |
| [Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-get-visibility) \(formerly Azure Sentinel\) | ✓ | Not supported in Microsoft Sentinel | ✓ |

> **Note:** New providers are continuously onboarding to the Microsoft Graph security ecosystem. To request new providers or for extended support from existing providers, [file an issue in the Microsoft Graph security GitHub repo](https://github.com/microsoftgraph/security-api-solutions/issues/new).

\* File issue: Alert status gets updated across Microsoft Graph security API integrated applications but not reflected in the provider's management experience.

\*\* Microsoft Defender for Endpoint requires additional [user roles](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/user-roles) to those required by the Microsoft Graph security API. Only the users in both Microsoft Defender for Endpoint and Microsoft Graph security API roles can access the Microsoft Defender for Endpoint data. Because application-only authentication isn't limited by this, we recommend that you use an application-only authentication token.

\*\*\* Microsoft Defender for Identity alerts are available via the Microsoft Defender for Cloud Apps integration. This means you get Microsoft Defender for Identity alerts only if you joined Unified SecOps and connected Microsoft Defender for Identity to Microsoft Defender for Cloud Apps. Learn more about [how to integrate Microsoft Defender for Identity and Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-for-identity/mcas-integration).

## Attack simulation and training

[Attack simulation and training](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training) is part of [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/defender-for-office-365?view=o365-worldwide&preserve-view=true). This service lets users in a tenant experience a realistic benign phishing attack and learn from it. Social engineering simulation and training experiences for end users help reduce the risk of users being breached via those attack techniques. The attack simulation and training API enables tenant administrators to view launched [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) exercises and trainings, and get [reports](https://learn.microsoft.com/en-us/graph/api/resources/report-m365defender-reports-overview?view=graph-rest-1.0) on derived insights into online behaviors of users in the phishing simulations.

## eDiscovery

[Microsoft Purview eDiscovery](https://learn.microsoft.com/en-us/purview/edisc) provides an end-to-end workflow to preserve, collect, analyze, review, and export content that's responsive to your organization's internal and external investigations.

## Audit log query

[Microsoft Purview Audit](https://learn.microsoft.com/en-us/purview/audit-solutions-overview) provides an integrated solution to help organizations effectively respond to security events, forensic investigations, internal investigations, and compliance obligations. Thousands of user and admin operations performed in dozens of Microsoft 365 services and solutions are captured, recorded, and retained in your organization's unified audit log. Audit records for these events are searchable by security ops, IT admins, insider risk teams, and compliance and legal investigators in your organization. This capability provides visibility into the activities performed across your Microsoft 365 organization.

## Identities

### Health issues

The Microsoft Defender for Identity health issues API allows you to monitor the health status of your sensors and agents across your hybrid identity infrastructure. You can use the health issues API to retrieve information about the current health issues of your sensors, such as the issue type, status, configuration, and severity. You can also use this API to identify and resolve any issues that might affect the functionality or security of your sensors and agents.

> **Note:** The Microsoft Defender for Identity health issues API is only available on the Defender for Identity plan or Microsoft 365 E5/A5/G5/F5 Security service plans.

### Sensors

The Defender for Identity sensors management APIs allows you to:

- Create detailed reports of the sensors in your workspace, including information about the server name, sensor version, type, state, and health status.
- Manage sensor settings, such as adding descriptions, enabling or disabling delayed updates, and specifying the domain controller that the sensor connects to for querying Entra ID.
- Identify sensors that are ready to be activated.
- Define whether the sensors in your infrastructure are to be activated automatically or manually.
- Identify servers that are ready to be activated with the unified agent.
- Enable or disable the automatic activation of eligible servers for the unified agent.
- Activate or deactivate the unified agent on eligible servers.
- Enable or disable the automatic enabling of the required events auditing configuration during the sensor’s activation.

### identityAccounts

The [identityAccounts resource and related APIs](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0) allows you to retrieve details of users that are flagged by Microsoft Defender for Identity alerts, and apply actions such as disabling accounts and resetting the user password for the compromised user.

## Incidents

An [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) is a collection of correlated [alerts](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) and associated data that make up the story of an attack. Incident management is part of Microsoft 365 Defender and is available in the Microsoft 365 Defender portal \([https://security.microsoft.com/](https://security.microsoft.com/)\).

Microsoft 365 services and apps create alerts when they detect a suspicious or malicious event or activity. Individual alerts provide valuable clues about a completed or ongoing attack. However, attacks typically employ various techniques against different types of entities, such as devices, users, and mailboxes. The result is multiple alerts for multiple entities in your tenant.

Because piecing the individual alerts together to gain insight into an attack can be challenging and time-consuming, Microsoft 365 Defender automatically aggregates the alerts and their associated information into an [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0).

Grouping related alerts into an incident gives you a comprehensive view of an attack. For example, you can see:

- Where the attack started.
- What tactics were used.
- How far the attack went into your tenant.
- The scope of the attack, such as how many devices, users, and mailboxes were impacted.
- All of the data associated with the attack.

The [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) resource and its APIs allow you to sort through incidents to create an informed cybersecurity response. It exposes a collection of incidents, with their related [alerts](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0), that were flagged in your network, within the time range you specified in your environment retention policy.

## Information protection

The Microsoft Graph threat assessment API helps organizations assess the threat received by any user in a tenant. This empowers customers to report spam emails, phishing URLs, or malware attachments they receive to Microsoft. The policy check result and rescan result can help tenant administrators understand the threat scanning verdict and adjust their organizational policy.

## Records management

Most organizations need to manage data to proactively comply with industry regulations and internal policies, reduce risk in the event of litigation or a security breach, and let people effectively and agilely share knowledge that is current and relevant to them. You can use the [records management APIs](https://learn.microsoft.com/en-us/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-1.0) to systematically apply [retention labels](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) to different types of content that require different retention settings. For example, you can configure the start of the retention period from when the content was created, last modified, labeled, or when an event occurs for a particular event type. Further, you can use [file plan descriptors](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0) to improve the manageability of these retention labels.

## Secure Score

[Microsoft Secure Score](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/A-new-home-and-an-all-new-look-for-Microsoft-Secure-Score/ba-p/529641) is a security analytics solution that gives you visibility into your security portfolio and how to improve it. With a single score, you can better understand what you did to reduce your risk in Microsoft solutions. You can also compare your score with other organizations and see how your score has been trending over time. The Microsoft Graph security [secureScore](https://learn.microsoft.com/en-us/graph/api/resources/securescore?view=graph-rest-1.0) and [secureScoreControlProfile](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofile?view=graph-rest-1.0) entities help you balance your organization's security and productivity needs while enabling the appropriate mix of security features. You can also project what your score would be after you adopt security features.

## Threat intelligence

Microsoft Defender Threat Intelligence delivers world-class threat intelligence to help protect your organization from modern cyber threats. You can use Threat Intelligence to identify adversaries and their operations, accelerate detection and remediation, and enhance your security investments and workflows.

The threat intelligence APIs allow you to operationalize intelligence found within the user interface. This includes finished intelligence in the forms of articles and intel profiles, machine intelligence such as IoCs and reputation verdicts, and enrichment data such as passive DNS, cookies, components, and trackers.

## Common use cases

The following are some of the most popular requests for working with the Microsoft Graph security API.

| **Use cases** | **REST resources** | **Try it in Graph Explorer** |
| :--- | :--- | :--- |
| Update secure score control profiles | [Update secureScoreControlProfile](https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofile-update?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/secureScoreControlProfiles/{id}](https://developer.microsoft.com/graph/graph-explorer?request=security/secureScoreControlProfiles/%7Bid%7D&method=PATCH&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| **Alerts and incidents** |  |  |
| List alerts | [List alerts](https://learn.microsoft.com/en-us/graph/api/security-list-alerts_v2?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/alerts\_v2](https://developer.microsoft.com/graph/graph-explorer?request=security/alerts_v2&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| Update alert | [Update alert](https://learn.microsoft.com/en-us/graph/api/security-alert-update?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/alerts/{id}](https://developer.microsoft.com/graph/graph-explorer?request=security/alerts/%7Bid%7D&method=PATCH&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| List incidents | [List incidents](https://learn.microsoft.com/en-us/graph/api/security-list-incidents?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/incidents](https://developer.microsoft.com/graph/graph-explorer?request=security/incidents&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| List incidents with alerts | [List incidents](https://learn.microsoft.com/en-us/graph/api/security-list-incidents?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/incidents?$expand=alerts](https://developer.microsoft.com/graph/graph-explorer?request=security/incidents?$expand=alerts&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| Update incident | [Update incident](https://learn.microsoft.com/en-us/graph/api/security-incident-update?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/incidents/{id}](https://developer.microsoft.com/graph/graph-explorer?request=security/incidents/%7Bid%7D&method=PATCH&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| **eDiscovery** |  |  |
| List eDiscovery cases | [List eDiscoveryCases](https://learn.microsoft.com/en-us/graph/api/security-casesroot-list-ediscoverycases?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/cases/eDiscoveryCases](https://developer.microsoft.com/graph/graph-explorer?request=security%2Fcases%2FeDiscoverycases&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| List eDiscovery case operations | [List caseOperations](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-operations?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{id}/operations](https://developer.microsoft.com/graph/graph-explorer?request=security%2Fcases%2FeDiscoverycases%2F%7Bid%7D%2Foperations&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| **Identities** |  |  |
| List health issues | [List health issues](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-healthissues?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/identities/healthIssues](https://developer.microsoft.com/graph/graph-explorer?request=security/identities/healthIssues&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| List sensors | [List sensors](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-sensors?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/identities/sensors](https://developer.microsoft.com/graph/graph-explorer?request=security/identities/sensors&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| **Legacy alerts** |  |  |
| List alerts | [List alerts](https://learn.microsoft.com/en-us/graph/api/alert-list?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/alerts](https://developer.microsoft.com/graph/graph-explorer?request=security/alerts&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| Update alerts | [Update alert](https://learn.microsoft.com/en-us/graph/api/alert-update?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/alerts/{alert-id}](https://developer.microsoft.com/graph/graph-explorer?request=security/alerts/%7Balert-id%7D&method=PATCH&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| **Secure scores** |  |  |
| List secure scores | [List secureScores](https://learn.microsoft.com/en-us/graph/api/security-list-securescores?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/secureScores](https://developer.microsoft.com/graph/graph-explorer?request=security/secureScores&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| Get secure score | [Get secureScore](https://learn.microsoft.com/en-us/graph/api/securescore-get?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/secureScores/{id}](https://developer.microsoft.com/graph/graph-explorer?request=security/secureScores/%7Bid%7D&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| List secure score control profiles | [List secureScoreControlProfiles](https://learn.microsoft.com/en-us/graph/api/security-list-securescorecontrolprofiles?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/secureScoreControlProfiles](https://developer.microsoft.com/graph/graph-explorer?request=security/secureScoreControlProfiles&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |
| Get secure score control profile | [Get secureScoreControlProfile](https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofile-get?view=graph-rest-1.0) | [https://graph.microsoft.com/v1.0/security/secureScoreControlProfiles/{id}](https://developer.microsoft.com/graph/graph-explorer?request=security/secureScoreControlProfiles/%7Bid%7D&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) |

You can use Microsoft Graph [change notifications](https://learn.microsoft.com/en-us/graph/change-notifications-overview) to subscribe to and receive notifications about updates to Microsoft Graph security entities.

## Resources

Code and contribute to these Microsoft Graph security API samples:

- [ASP.NET \(C#\) sample](https://github.com/microsoftgraph/aspnet-security-api-sample)
- [Python sample](https://github.com/microsoftgraph/python-security-rest-sample)
- [Node.js \(JavaScript\) sample](https://github.com/microsoftgraph/nodejs-security-sample)

Engage with the community:

- [Join the tech community](https://techcommunity.microsoft.com/t5/microsoft-graph-security-api/bd-p/SecurityGraphAPI)
- [Discuss on StackOverflow](https://stackoverflow.com/questions/tagged/microsoft-graph-security)

## Next steps

The Microsoft Graph security API can open up new ways for you to engage with different security solutions from Microsoft and its partners. Follow these steps to get started:

- Drill down into [alerts](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0), [secureScore](https://learn.microsoft.com/en-us/graph/api/resources/securescore?view=graph-rest-1.0), and [secureScoreControlProfiles](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofile?view=graph-rest-1.0).
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer). Under **Sample Queries**, choose **show more samples** and set the Security category to **on**.
- Try [subscribing to and receiving notifications](https://learn.microsoft.com/en-us/graph/change-notifications-overview) on entity changes.

## Related content

[Code and contribute](https://github.com/microsoftgraph/security-api-solutions/blob/master/CONTRIBUTING.md) to this Microsoft Graph security API sample:

- [PowerShell sample](https://learn.microsoft.com/en-us/powershell/scripting/developer/prog-guide/windows-powershell-sample-code)

Explore other options to connect with the Microsoft Graph security API:

- [Microsoft Graph security connectors for Logic Apps, Flow and Power Apps](https://learn.microsoft.com/en-us/azure/connectors/connectors-integrate-security-operations-create-api-microsoft-graph-security)
- [Jupyter Notebook samples](https://learn.microsoft.com/en-us/azure/machine-learning/samples-notebooks)

Engage with the community:

- [Join the tech community](https://techcommunity.microsoft.com/t5/microsoft-graph-security-api/bd-p/SecurityGraphAPI)
- [Discuss on StackOverflow](https://stackoverflow.com/questions/tagged/microsoft-graph-security)
