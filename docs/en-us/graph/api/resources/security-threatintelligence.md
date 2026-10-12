<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-threatintelligence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# threatIntelligence resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Provides APIs to retrieve threat intelligence information, such as about a host or an article on a threat.

The Microsoft Graph threat intelligence API delivers world-class threat intelligence to help protect your organization from modern cyber threats. Using threat intelligence APIs, you can identify adversaries and their operations, accelerate detection and remediation, and enhance your security investments and workflows.

The threat intelligence API allows you to operationalize intelligence found within the user interface. This includes finished intelligence in the forms of articles and intel profiles, machine intelligence including indicators of compromise \(IoCs\) and reputation verdicts, and finally, enrichment data including passive DNS, cookies, components, and trackers.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List articles](https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-articles?view=graph-rest-1.0) | [microsoft.graph.security.article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) collection | Get a list of **article** objects, including their properties and relationships. |
| [List intelProfiles](https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-intelprofiles?view=graph-rest-1.0) | [microsoft.graph.security.intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0) collection | Get a list of **intelligenceProfile** resources. |
| [Get hostPort](https://learn.microsoft.com/en-us/graph/api/security-hostport-get?view=graph-rest-1.0) | [microsoft.graph.security.hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) | Get the properties and relationships of a **hostPort** object. |
| [List sslCertificates](https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-sslcertificates?view=graph-rest-1.0) | [microsoft.graph.security.sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) collection | Get a list of [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) objects and their properties. |
| [List whoisRecords](https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-whoisrecords?view=graph-rest-1.0) | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-vulnerability?view=graph-rest-1.0) | Get a list of [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) objects. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| articleIndicators | [microsoft.graph.security.articleIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-articleindicator?view=graph-rest-1.0) collection | Refers to indicators of threat or compromise highlighted in an [article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0).  <br>**Note**: List retrieval is not yet supported. |
| articles | [microsoft.graph.security.article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) collection | A list of **article** objects. |
| hostComponents | [microsoft.graph.security.hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) collection | Retrieve details about [hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| hostCookies | [microsoft.graph.security.hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) collection | Retrieve details about [hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| hostPairs | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | Retrieve details about [hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| hostPorts | [microsoft.graph.security.hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) collection | Retrieve details about [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| hostSslCertificates | [microsoft.graph.security.hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) collection | Retrieve details about [hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| hostTrackers | [microsoft.graph.security.hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) collection | Retrieve details about [hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| hosts | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) collection | Refers to [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) objects that Microsoft Threat Intelligence has observed.  <br>**Note**: List retrieval is not yet supported. |
| intelProfileIndicators | [microsoft.graph.security.intelligenceProfileIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0) collection | Refers to indicators of threat or compromise highlighted in an [intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0).  <br>**Note**: List retrieval is not yet supported. |
| intelProfiles | [microsoft.graph.security.intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0) collection | A list of **intelligenceProfile** objects. |
| passiveDnsRecords | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Retrieve details about [passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| sslCertificates | [microsoft.graph.security.sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) collection | Retrieve details about [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) objects.  <br>**Note**: List retrieval is not yet supported. |
| subdomains | [microsoft.graph.security.subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0) collection | Retrieve details about the [subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0).  <br>**Note**: List retrieval is not yet supported. |
| vulnerabilities | [microsoft.graph.security.vulnerability](https://learn.microsoft.com/en-us/graph/api/resources/security-vulnerability?view=graph-rest-1.0) collection | Retrieve details about [vulnerabilities](https://learn.microsoft.com/en-us/graph/api/resources/security-vulnerability?view=graph-rest-1.0).  <br>**Note**: List retrieval is not yet supported. |
| whoisHistoryRecords | [microsoft.graph.security.whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) collection | Retrieve details about [whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) objects.  <br>**Note:** List retrieval is not yet supported. |
| whoisRecords | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) collection | A list of [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) objects. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.threatIntelligence"
}
```
