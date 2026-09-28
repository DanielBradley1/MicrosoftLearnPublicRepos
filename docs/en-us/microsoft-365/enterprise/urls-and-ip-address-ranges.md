<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# Microsoft 365 URLs and IP address ranges

Microsoft 365 requires connectivity to the Internet. The endpoints in this article should be reachable for customers using Microsoft 365 plans, including Government Community Cloud \(GCC\).

*Microsoft 365 Worldwide \(+GCC\)* \| [Microsoft 365 operated by 21 Vianet](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges-21vianet?view=o365-worldwide) \| [Microsoft 365 U.S. Government DoD](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints?view=o365-worldwide) \| [Microsoft 365 U.S. Government GCC High](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints?view=o365-worldwide) \|

| Notes | Download | Use |
| --- | --- | --- |
| **Last updated:** 08/14/2026 - [Change Log subscription](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) | **Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list. | **Use:** our proxy [PAC files](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints?view=o365-worldwide#pacfiles) |

Start with [Managing Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints?view=o365-worldwide) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated as needed at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This cadence allows for customers who don't yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you're using a script or a network device to access this data, you should go to the [Web service](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-ip-web-service?view=o365-worldwide) directly.

Endpoint data below lists requirements for connectivity from a user's machine to Microsoft 365. For detail on IP addresses used for network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections, see [other endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls?view=o365-worldwide) for more information.

The endpoints are grouped into four service areas representing the three primary workloads and a set of common resources. The groups may be used to associate traffic flows with a particular application, however given that features often consume endpoints across multiple workloads, these groups can't effectively be used to restrict access.

Data columns shown are:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.
- **Category**: Shows whether the endpoint set is categorized as **Optimize**, **Allow**, or **Default**. This column also lists which endpoint sets are required to have network connectivity. For endpoint sets that aren't required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked.

  You can read about these categories and guidance for their management in [Optimizing connectivity to Microsoft 365 services](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles?view=o365-worldwide#optimizing-connectivity-to-microsoft-365-services).
- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Microsoft 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute isn't supported for this endpoint set.

  Some routes may be advertised in more than one BGP community, making it possible for endpoints within a given IP range to traverse the ER circuit, but still be unsupported. In all cases, the value of a given endpoint set's ER column should be respected.
- **Addresses**: Lists the FQDNs or wildcard domain names and IP address ranges for the endpoint set. Note that an IP address range is in CIDR format and may include many individual IP addresses in the specified network.
- **Ports**: Lists the TCP or UDP ports that are combined with listed IP addresses to form the network endpoint. You may notice some duplication in IP address ranges where there are different ports listed.

## [Microsoft 365 Unified Domains](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain?view=o365-worldwide)

Note

In response to customer feedback and to streamline endpoint management, Microsoft has initiated the process of consolidating Microsoft 365 apps and services into a select group of dedicated, secured, and purpose-managed domains within the **.microsoft** top level domain \(TLD\).

To avoid connectivity issues for users, ensure that the following essential domains are included in your allowlist and that connectivity to these domains isn't blocked.

| ID | Category | Domain name | Purpose | Ports |
| --- | --- | --- | --- | --- |
| 184 | Required | `*.cloud.microsoft` | Dedicated to authenticated user facing Microsoft SaaS product experiences. | **TCP:** 443  <br>**UDP:** 443 |
| 184 | Required | `*.static.microsoft` | Dedicated to static \(not customer generated\) content hosted on CDNs. | **TCP:** 443  <br>**UDP:** 443 |
| 184 | Required | `*.usercontent.microsoft` | Content used in Microsoft 365 experiences that requires domain isolation from applications. | **TCP:** 443  <br>**UDP:** 443 |

## Exchange Online

| ID | Category | ER | Addresses | Ports |
| --- | --- | --- | --- | --- |
| 1 | Optimize  <br>Required | Yes | `outlook.cloud.microsoft, outlook.office.com, outlook.office365.com`  <br>`13.107.6.152/31, 13.107.18.10/31, 13.107.128.0/22, 23.103.160.0/20, 40.96.0.0/13, 40.104.0.0/15, 52.96.0.0/14, 131.253.33.215/32, 132.245.0.0/16, 150.171.32.0/22, 204.79.197.215/32, 2603:1006::/40, 2603:1016::/36, 2603:1026::/36, 2603:1036::/36, 2603:1046::/36, 2603:1056::/36, 2620:1ec:4::152/128, 2620:1ec:4::153/128, 2620:1ec:c::10/128, 2620:1ec:c::11/128, 2620:1ec:d::10/128, 2620:1ec:d::11/128, 2620:1ec:8f0::/46, 2620:1ec:900::/46, 2620:1ec:a92::152/128, 2620:1ec:a92::153/128` | **TCP:** 443, 80  <br>**UDP:** 443 |
| 2 | Allow  <br>Optional  <br>**Notes:** POP3, IMAP4, SMTP Client traffic | Yes | `outlook.office365.com, smtp.office365.com`  <br>`13.107.6.152/31, 13.107.18.10/31, 13.107.128.0/22, 23.103.160.0/20, 40.96.0.0/13, 40.104.0.0/15, 52.96.0.0/14, 131.253.33.215/32, 132.245.0.0/16, 150.171.32.0/22, 204.79.197.215/32, 2603:1006::/40, 2603:1016::/36, 2603:1026::/36, 2603:1036::/36, 2603:1046::/36, 2603:1056::/36, 2620:1ec:4::152/128, 2620:1ec:4::153/128, 2620:1ec:c::10/128, 2620:1ec:c::11/128, 2620:1ec:d::10/128, 2620:1ec:d::11/128, 2620:1ec:8f0::/46, 2620:1ec:900::/46, 2620:1ec:a92::152/128, 2620:1ec:a92::153/128` | **TCP:** 587, 993, 995, 143 |
| 8 | Default  <br>Required | No | `*.outlook.com, autodiscover.<tenant>.onmicrosoft.com` | **TCP:** 443, 80 |
| 9 | Allow  <br>Required | Yes | `*.protection.outlook.com`  <br>`40.92.0.0/15, 40.107.0.0/16, 52.100.0.0/14, 52.238.78.88/32, 104.47.0.0/17, 2a01:111:f400::/48, 2a01:111:f403::/48` | **TCP:** 443 |
| 10 | Allow  <br>Required | Yes | `*.mail.protection.outlook.com, *.mx.microsoft`  <br>`40.92.0.0/15, 40.107.0.0/16, 52.100.0.0/14, 104.47.0.0/17, 2a01:111:f400::/48, 2a01:111:f403::/48` | **TCP:** 25 |

## SharePoint Online and OneDrive for Business

| ID | Category | ER | Addresses | Ports |
| --- | --- | --- | --- | --- |
| 31 | Optimize  <br>Required | Yes | `*.sharepoint.com`  <br>`13.107.136.0/22, 40.108.128.0/17, 52.104.0.0/14, 104.146.128.0/17, 150.171.40.0/22, 2603:1061:1300::/40, 2603:1063:6000::/35, 2620:1ec:8f8::/46, 2620:1ec:908::/46, 2a01:111:f402::/48` | **TCP:** 443, 80  <br>**UDP:** 443 |
| 32 | Default  <br>Optional  <br>**Notes:** OneDrive for Business: supportability, telemetry, APIs, and embedded email links | No | `storage.live.com` | **TCP:** 443 |
| 35 | Default  <br>Required | No | `*.wns.windows.com, admin.onedrive.com, officeclient.microsoft.com` | **TCP:** 443, 80 |
| 36 | Default  <br>Required | No | `g.live.com, oneclient.sfx.ms` | **TCP:** 443, 80 |
| 37 | Default  <br>Required | No | `*.sharepointonline.com, spoprod-a.akamaihd.net` | **TCP:** 443, 80 |
| 39 | Default  <br>Required | No | `*.svc.ms` | **TCP:** 443, 80 |

## Microsoft Teams

| ID | Category | ER | Addresses | Ports |
| --- | --- | --- | --- | --- |
| 11 | Optimize  <br>Required | Yes | `52.112.0.0/14, 52.122.0.0/15, 2603:1063::/38` | **UDP:** 3478, 3479, 3480, 3481 |
| 12 | Allow  <br>Required | Yes | `*.lync.com, *.teams.cloud.microsoft, *.teams.microsoft.com, teams.cloud.microsoft, teams.microsoft.com`  <br>`52.112.0.0/14, 52.122.0.0/15, 2603:1027::/48, 2603:1037::/48, 2603:1047::/48, 2603:1057::/48, 2603:1063::/38, 2620:1ec:6::/48, 2620:1ec:40::/42` | **TCP:** 443, 80  <br>**UDP:** 443 |
| 16 | Default  <br>Required | No | `*.keydelivery.mediaservices.windows.net, *.streaming.mediaservices.windows.net` | **TCP:** 443 |
| 17 | Default  <br>Required | No | `aka.ms` | **TCP:** 443 |
| 19 | Default  <br>Optional  <br>**Notes:** For end user and customer owned device updates | No | `adl.windows.com` | **TCP:** 443, 80 |
| 27 | Default  <br>Required | No | `join.secure.skypeassets.com, mlccdnprod.azureedge.net` | **TCP:** 443 |
| 127 | Default  <br>Required | No | `*.skype.com` | **TCP:** 443, 80 |

## Microsoft 365 Common and Office Online

| ID | Category | ER | Addresses | Ports |
| --- | --- | --- | --- | --- |
| 46 | Allow  <br>Required | Yes | `*.officeapps.live.com, *.online.office.com, office.live.com`  <br>`13.107.6.171/32, 13.107.18.15/32, 13.107.140.6/32, 52.108.0.0/14, 52.244.37.168/32, 2603:1006:1400::/40, 2603:1016:2400::/40, 2603:1026:2400::/40, 2603:1036:2400::/40, 2603:1046:1400::/40, 2603:1056:1400::/40, 2603:1063:2000::/38, 2620:1ec:c::15/128, 2620:1ec:8fc::6/128, 2620:1ec:a92::171/128, 2a01:111:f100:2000::a83e:3019/128, 2a01:111:f100:2002::8975:2d79/128, 2a01:111:f100:2002::8975:2da8/128, 2a01:111:f100:7000::6fdd:6cd5/128, 2a01:111:f100:a004::bfeb:88cf/128` | **TCP:** 443, 80 |
| 47 | Default  <br>Required | No | `*.office.net` | **TCP:** 443, 80  <br>**UDP:** 443 |
| 49 | Default  <br>Required | No | `*.onenote.com` | **TCP:** 443 |
| 50 | Default  <br>Optional  <br>**Notes:** OneNote notebooks \(wildcards\) | No | `*.microsoft.com` | **TCP:** 443 |
| 51 | Default  <br>Required | No | `*cdn.onenote.net` | **TCP:** 443 |
| 53 | Default  <br>Required | No | `ajax.aspnetcdn.com, apis.live.net, officeapps.live.com, www.onedrive.com` | **TCP:** 443 |
| 56 | Allow  <br>Required | Yes | `*.auth.microsoft.com, *.msftidentity.com, *.msidentity.com, account.activedirectory.windowsazure.com, accounts.accesscontrol.windows.net, adminwebservice.microsoftonline.com, api.passwordreset.microsoftonline.com, autologon.microsoftazuread-sso.com, becws.microsoftonline.com, ccs.login.microsoftonline.com, clientconfig.microsoftonline-p.net, companymanager.microsoftonline.com, device.login.microsoftonline.com, graph.microsoft.com, graph.windows.net, login-us.microsoftonline.com, login.microsoft.com, login.microsoftonline-p.com, login.microsoftonline.com, login.windows.net, logincert.microsoftonline.com, loginex.microsoftonline.com, nexus.microsoftonline-p.com, passwordreset.microsoftonline.com, provisioningapi.microsoftonline.com`  <br>`20.20.32.0/19, 20.190.128.0/18, 20.231.128.0/19, 40.126.0.0/18, 2603:1006:2000::/48, 2603:1007:200::/48, 2603:1016:1400::/48, 2603:1017::/48, 2603:1026:3000::/48, 2603:1027:1::/48, 2603:1036:3000::/48, 2603:1037:1::/48, 2603:1046:2000::/48, 2603:1047:1::/48, 2603:1056:2000::/48, 2603:1057:2::/48` | **TCP:** 443, 80 |
| 59 | Default  <br>Required | No | `*.hip.live.com, *.microsoftonline-p.com, *.microsoftonline.com, *.msauth.net, *.msauthimages.net, *.msecnd.net, *.msftauth.net, *.msftauthimages.net, *.phonefactor.net, enterpriseregistration.windows.net` | **TCP:** 443, 80 |
| 64 | Allow  <br>Required | Yes | `*.protection.office.com, *.security.microsoft.com, compliance.microsoft.com, defender.microsoft.com, protection.office.com, purview.microsoft.com, security.microsoft.com`  <br>`13.107.6.192/32, 13.107.9.192/32, 2620:1ec:4::192/128, 2620:1ec:a92::192/128` | **TCP:** 443 |
| 66 | Default  <br>Required | No | `*.portal.cloudappsecurity.com` | **TCP:** 443 |
| 69 | Default  <br>Required | No | `*.aria.microsoft.com, *.events.data.microsoft.com` | **TCP:** 443 |
| 70 | Default  <br>Required | No | `*.o365weve.com, amp.azure.net, appsforoffice.microsoft.com, assets.onestore.ms, auth.gfx.ms, c1.microsoft.com, dgps.support.microsoft.com, docs.microsoft.com, msdn.microsoft.com, platform.linkedin.com, prod.msocdn.com, shellprod.msocdn.com, support.microsoft.com, technet.microsoft.com` | **TCP:** 443 |
| 71 | Default  <br>Required | No | `*.office365.com` | **TCP:** 443, 80 |
| 73 | Default  <br>Required | No | `*.aadrm.com, *.azurerms.com, *.informationprotection.azure.com, ecn.dev.virtualearth.net, informationprotection.hosting.portal.azure.net` | **TCP:** 443 |
| 75 | Default  <br>Optional  <br>**Notes:** Graph.windows.net, Office 365 Management Pack for Operations Manager, SecureScore, Azure AD Device Registration, Forms, StaffHub, Application Insights, captcha services | No | `*.sharepointonline.com, dc.services.visualstudio.com, mem.gfx.ms` | **TCP:** 443 |
| 78 | Default  <br>Optional  <br>**Notes:** Some Office 365 features require endpoints within these domains \(including CDNs\). Many specific FQDNs within these wildcards have been published recently as we work to either remove or better explain our guidance relating to these wildcards. | No | `*.microsoft.com, *.msocdn.com, *.onmicrosoft.com` | **TCP:** 443, 80 |
| 79 | Default  <br>Required | No | `o15.officeredir.microsoft.com, officepreviewredir.microsoft.com, officeredir.microsoft.com, r.office.microsoft.com` | **TCP:** 443, 80 |
| 83 | Default  <br>Required | No | `activation.sls.microsoft.com` | **TCP:** 443 |
| 84 | Default  <br>Required | No | `crl.microsoft.com` | **TCP:** 443, 80 |
| 86 | Default  <br>Required | No | `office15client.microsoft.com, officeclient.microsoft.com` | **TCP:** 443 |
| 89 | Default  <br>Required | No | `go.microsoft.com` | **TCP:** 443, 80 |
| 91 | Default  <br>Required | No | `ajax.aspnetcdn.com, cdn.odc.officeapps.live.com` | **TCP:** 443, 80 |
| 92 | Default  <br>Required | No | `officecdn.microsoft.com, otelrules.azureedge.net` | **TCP:** 443, 80 |
| 93 | Default  <br>Optional  <br>**Notes:** ProPlus: auxiliary URLs | No | `*.virtualearth.net, c.bing.net, ocos-office365-s2s.msedge.net, tse1.mm.bing.net, www.bing.com` | **TCP:** 443, 80 |
| 95 | Default  <br>Optional  <br>**Notes:** Outlook for Android and iOS | No | `*.acompli.net, *.outlookmobile.com` | **TCP:** 443 |
| 96 | Default  <br>Optional  <br>**Notes:** Outlook for Android and iOS: Authentication | No | `login.windows-ppe.net` | **TCP:** 443 |
| 97 | Default  <br>Optional  <br>**Notes:** Outlook for Android and iOS: Consumer Outlook.com and OneDrive integration | No | `account.live.com, login.live.com` | **TCP:** 443 |
| 114 | Default  <br>Optional  <br>**Notes:** Office Mobile URLs | No | `*.appex-rf.msn.com, *.appex.bing.com, c.bing.com, c.live.com, partnerservices.getmicrosoftkey.com, signup.live.com` | **TCP:** 443, 80 |
| 116 | Default  <br>Optional  <br>**Notes:** Office for iPad URLs | No | `account.live.com, auth.gfx.ms, login.live.com` | **TCP:** 443, 80 |
| 117 | Default  <br>Optional  <br>**Notes:** Viva Engage | No | `<tenant>.yammer.com, <tenant>.yammerusercontent.com` | **TCP:** 443 |
| 118 | Default  <br>Optional  <br>**Notes:** Viva Engage Assets CDN | No | `*.assets-yammer.com` | **TCP:** 443 |
| 121 | Default  <br>Optional  <br>**Notes:** Planner: auxiliary URLs | No | `www.outlook.com` | **TCP:** 443, 80 |
| 122 | Default  <br>Optional  <br>**Notes:** Sway CDNs | No | `eus-www.sway-cdn.com, eus-www.sway-extensions.com, wus-www.sway-cdn.com, wus-www.sway-extensions.com` | **TCP:** 443 |
| 124 | Default  <br>Optional  <br>**Notes:** Sway | No | `sway.com, www.sway.com` | **TCP:** 443 |
| 125 | Default  <br>Required | No | `*.entrust.net, *.geotrust.com, *.omniroot.com, *.public-trust.com, *.symcb.com, *.symcd.com, *.verisign.com, *.verisign.net, cacerts.digicert.com, cert.int-x3.letsencrypt.org, crl.globalsign.com, crl.globalsign.net, crl.identrust.com, crl3.digicert.com, crl4.digicert.com, isrg.trustid.ocsp.identrust.com, mscrl.microsoft.com, ocsp.digicert.com, ocsp.globalsign.com, ocsp.msocsp.com, ocsp2.globalsign.com, ocspx.digicert.com, oneocsp.microsoft.com, secure.globalsign.com, www.digicert.com, www.microsoft.com` | **TCP:** 443, 80 |
| 126 | Default  <br>Optional  <br>**Notes:** Connection to the speech service is required for Office Dictation features. If connectivity is not allowed, Dictation will be disabled. | No | `officespeech.platform.bing.com` | **TCP:** 443 |
| 147 | Default  <br>Required | No | `*.office.com, www.microsoft365.com` | **TCP:** 443, 80 |
| 152 | Default  <br>Optional  <br>**Notes:** These endpoints enable the Office Scripts functionality in Office clients available through the Automate tab and the Python in Excel functionality available through the Formulas tab. The Office Scripts feature can also be disabled through the Office 365 Admin portal. For admin controls related to Python in Excel, see [Data security and Python in Excel](https://support.microsoft.com/office/data-security-and-python-in-excel-33cc88a4-4a87-485e-9ff9-f35958278327). | No | `*.microsoftusercontent.com` | **TCP:** 443 |
| 153 | Default  <br>Required | No | `*.azure-apim.net, *.flow.microsoft.com, *.powerapps.com, *.powerautomate.com` | **TCP:** 443 |
| 156 | Default  <br>Required | No | `*.activity.windows.com, activity.windows.com` | **TCP:** 443 |
| 158 | Default  <br>Required | No | `*.cortana.ai` | **TCP:** 443 |
| 159 | Default  <br>Required | No | `admin.microsoft.com` | **TCP:** 443, 80 |
| 160 | Default  <br>Required | No | `cdn.odc.officeapps.live.com, cdn.uci.officeapps.live.com` | **TCP:** 443, 80 |
| 184 | Default  <br>Required | No | `*.cloud.microsoft` | **TCP:** 443  <br>**UDP:** 443 |
| 193 | Default  <br>Required | No | `*.static.microsoft, *.usercontent.microsoft` | **TCP:** 443  <br>**UDP:** 443 |

Notes for this table:

- The Security and Compliance Center \(SCC\) provides support for Azure ExpressRoute for Microsoft 365. The same applies for many features exposed through the SCC such as Reporting, Auditing, eDiscovery \(Premium\), Unified DLP, and Data Governance. Two specific features, PST Import and eDiscovery Export, currently don't support Azure ExpressRoute with only Microsoft 365 route filters due to their dependency on Azure Blob Storage \(\*.blob.core.windows.net\). To consume those features, you need separate connectivity to Azure Blob Storage using any supportable Azure connectivity options, which include Internet connectivity or Azure ExpressRoute with Azure Public route filters. You have to evaluate establishing such connectivity for both of those features. The Microsoft 365 Information Protection team is aware of this limitation and is actively working to bring support for Azure ExpressRoute for Microsoft 365 as limited to Microsoft 365 route filters for both of those features.

## Related Topics

- [Other endpoints not included in the Microsoft 365 IP Address and URL Web service](https://learn.microsoft.com/en-us/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls?view=o365-worldwide)
- [Managing Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints?view=o365-worldwide)
- [General Microsoft Stream endpoints](https://learn.microsoft.com/en-us/stream/network-overview#general-microsoft-stream-endpoints)
- [Monitor Microsoft 365 connectivity](https://learn.microsoft.com/en-us/microsoft-365/enterprise/monitor-connectivity?view=o365-worldwide)
- [Client connectivity](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-networking-overview?view=o365-worldwide)
- [Content delivery networks](https://learn.microsoft.com/en-us/microsoft-365/enterprise/content-delivery-networks?view=o365-worldwide)
- [Microsoft Azure IP Ranges and Service Tags - Public Cloud](https://www.microsoft.com/en-us/download/details.aspx?id=56519)
- [Microsoft Azure IP Ranges and Service Tags - US Government Cloud](https://www.microsoft.com/en-us/download/details.aspx?id=57063)
- [Microsoft Azure IP Ranges and Service Tags - China Cloud](https://www.microsoft.com/en-us/download/details.aspx?id=57062)
- [Microsoft Public IP Space](https://www.microsoft.com/en-us/download/details.aspx?id=53602)
- [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
