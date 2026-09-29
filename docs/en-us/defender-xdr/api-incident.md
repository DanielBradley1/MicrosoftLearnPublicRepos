<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/api-incident -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# Microsoft Defender XDR incidents API and the incidents resource type

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview?view=graph-rest-1.0&preserve-view=true).

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

An [incident](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview) is a collection of related alerts that help describe an attack. Events from different entities in your organization are aggregated automatically by Microsoft Defender. You can use the incidents API to programmatically access your organization's incidents and related alerts.

## Quotas and resource allocation

You can request up to 50 calls per minute or 1,500 calls per hour. Each method also has its own quotas. For more information on method-specific quotas, see the respective article for the method you want to use.

A `429` HTTP response code indicates that you've reached a quota, either by number of requests sent, or by allotted running time. The response body includes the time until the quota you reached is reset.

## Permissions

The incidents API requires different kinds of permissions for each of its methods. For more information about required permissions, see the respective method's article.

## Methods

| Method | Return Type | Description |
| --- | --- | --- |
| [List incidents](https://learn.microsoft.com/en-us/defender-xdr/api-list-incidents) | [Incident](https://learn.microsoft.com/en-us/defender-xdr/api-incident) list | Get a list of incidents. |
| [Update incident](https://learn.microsoft.com/en-us/defender-xdr/api-update-incidents) | [Incident](https://learn.microsoft.com/en-us/defender-xdr/api-incident) | Update a specific incident. |
| [Get incident](https://learn.microsoft.com/en-us/defender-xdr/api-get-incident) | [Incident](https://learn.microsoft.com/en-us/defender-xdr/api-incident) | Get a single incident. |

## Request body, response, and examples

Refer to the respective method articles for more details on how to construct a request or parse a response, and for practical examples.

## Common properties

| Property | Type | Description |
| --- | --- | --- |
| incidentId | long | Incident unique ID. |
| redirectIncidentId | nullable long | The Incident ID the current Incident was merged to. |
| incidentName | string | The name of the Incident. |
| createdTime | DateTimeOffset | The date and time \(in UTC\) the Incident was created. |
| lastUpdateTime | DateTimeOffset | The date and time \(in UTC\) the incident was last updated. Use this property to identify incidents that changed after they were created. |
| assignedTo | string | Owner of the Incident. |
| severity | Enum | Severity of the incident. Possible values are: `UnSpecified`, `Informational`, `Low`, `Medium`, and `High`. Severity can change as alerts are added to or removed from the incident. The incident resource doesn't provide a history of severity changes. |
| status | Enum | Specifies the current status of the incident. Possible values are: `Active`, `InProgress`, `Resolved`, and `Redirected`. |
| classification | Enum | Specification of the incident. Possible values are: `TruePositive`, `Informational, expected activity`, and `FalsePositive`. |
| determination | Enum | Specifies the determination of the incident.<br><br>Possible determination values for each classification are:  <br><br><br><li> <b>True positive</b>: <code>Multistage attack</code> (MultiStagedAttack), <code>Malicious user activity</code> (MaliciousUserActivity), <code>Compromised account</code> (CompromisedUser) – consider changing the enum name in public api accordingly, <code>Malware</code> (Malware), <code>Phishing</code> (Phishing), <code>Unwanted software</code> (UnwantedSoftware), and <code>Other</code> (Other). </li><br><br><li> <b>Informational, expected activity:</b> <code>Security test</code> (SecurityTesting), <code>Line-of-business application</code> (LineOfBusinessApplication), <code>Confirmed activity</code> (ConfirmedUserActivity) - consider changing the enum name in public api accordingly, and <code>Other</code> (Other). </li><br><br><li>  <b>False positive:</b> <code>Not malicious</code> (Clean) - consider changing the enum name in public api accordingly, <code>Not enough data to validate</code> (InsufficientData), and <code>Other</code> (Other).</li> |
| tags | string list | List of Incident tags \(customTags only\). |
| comments | List of incident comments | Incident Comment object contains: comment string, createdBy string, and createTime date time. |
| alerts | alert list | List of related alerts. See examples at [List incidents](https://learn.microsoft.com/en-us/defender-xdr/api-list-incidents) API documentation. |

Note

Around August 29, 2022, previously supported alert determination values \(`Apt` and `SecurityPersonnel`\) will be deprecated and no longer available via the API.

## Related articles

- [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)
- [Microsoft Defender XDR APIs overview](https://learn.microsoft.com/en-us/defender-xdr/api-overview)
- [Incidents overview](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview)
- [List incidents API](https://learn.microsoft.com/en-us/defender-xdr/api-list-incidents)
- [Update incident API](https://learn.microsoft.com/en-us/defender-xdr/api-update-incidents)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
