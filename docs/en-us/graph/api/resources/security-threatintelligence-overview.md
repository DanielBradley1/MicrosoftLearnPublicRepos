<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-threatintelligence-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-01 -->

# Use the Microsoft Graph APIs for Microsoft Threat Intelligence

Organizations conducting threat infrastructure analysis and gathering threat intelligence can use the Microsoft Threat Intelligence APIs on Microsoft Graph to streamline triage, incident response, threat hunting, vulnerability management, and cyber threat intelligence analyst workflows. These APIs deliver world-class threat intelligence that helps protect your organization from modern cyber threats. You can identify adversaries and their operations, accelerate detection and remediation, and enhance your security investments and workflows.

These threat intelligence APIs allow you to operationalize intelligence found within the UI. This includes finished intelligence in the forms of articles and intel profiles, machine intelligence including indicators of compromise \(IoCs\) and reputation verdicts, and finally, enrichment data including passive DNS, cookies, components, and trackers.

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR and/or Microsoft Sentinel license. No separate license is required to access these APIs.

## Authorization

To call the threat intelligence APIs in Microsoft Graph, your app needs to acquire an access token. For details about access tokens, see [Get access tokens to call Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). Your app also needs the appropriate permissions. For more information, see [Threat intelligence permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#threat-intelligence-permissions).

### Required permissions

The following permissions are required to access the Microsoft Threat Intelligence APIs:

| Permission type | Permissions |
| :--- | :--- |
| Delegated \(work or school account\) | ThreatIntelligence.Read |
| Application | ThreatIntelligence.Read.All |

In addition, the calling user must have at minimum the **Security Reader** role assigned.

## Common use cases

The threat intelligence APIs fall into a few main categories:

- Written details about a threat or threat actor, such as [article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) and [intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0).
- Properties about a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0), such as **hostCookie**, **passiveDns**, or **whois**.

The following table lists some common use cases for the threat intelligence APIs.

| Use cases | REST resources | See also |
| :--- | :--- | :--- |
| Read articles about threat intelligence. | [article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) | [Methods of article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0#methods) |
| Read information about a host which is currently or was previously available on the internet and that Microsoft Threat Intelligence detected. You can get further details about a host including associated cookies, passive DNS entries, reputation, and more. | [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0),  <br>[hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0),  <br>[passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0),  <br>[hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0) | [Methods of host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0#methods) |
| Read information about web components observed on a **host**. | [hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) | [Methods of hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0#methods) |
| Read information about cookies observed on a **host**. | [hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) | [Methods of hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0#methods) |
| Discover referential host pairs observed about a host. Host pairs include details such as information about HTTP redirections, consumption of CSS or images from a host, and more. | [hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) | [Methods of hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0#methods) |
| Discover information about ports that Microsoft Threat Intelligence has observed on a **host**, including components on those ports, the number of times that a port has been observed, and what each host port banner response contains. | [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0),  <br>[hostPortComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostportcomponent?view=graph-rest-1.0),  <br>[hostPortBanner](https://learn.microsoft.com/en-us/graph/api/resources/security-hostportbanner?view=graph-rest-1.0) | [Methods of hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0#methods) |
| Read SSL certificate data observered on a host. This data includes information about the SSL certificate and the relationship between the host and the SSL certificate. | [hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0),  <br>[sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) | [Methods of hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0#methods) |
| Read Internet trackers observed on a **host**. | [hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) | [Methods of hosttracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0#methods) |
| Read intelligence profiles about threat actors and common tools of compromise. | [intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0),  <br>[intelligenceProfileIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0) | [Methods of intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0#methods) |
| Read passive DNS \(PDNS\) records about a **host**. | [passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) | [Methods of passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0#methods) |
| Read SSL certificate data. This information is standalone from the details about how the SSL certificate relates to a **host**. | [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) | [Methods of sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0#methods) |
| Read subdomain details for a **host**. | [subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0) | [Methods of subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0#methods) |
| Read details about a vulnerability. | [vulnerability](https://learn.microsoft.com/en-us/graph/api/resources/security-vulnerability?view=graph-rest-1.0) | [Methods of vulnerability](https://learn.microsoft.com/en-us/graph/api/resources/security-vulnerability?view=graph-rest-1.0#methods) |
| Read WHOIS details for a **host**. | [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) | [Methods of whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0#methods) |

## Next steps

The threat intelligence APIs in Microsoft Graph can help protect your organization from modern cyber threats. To learn more:

- Drill down on the methods and properties of the resources most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
