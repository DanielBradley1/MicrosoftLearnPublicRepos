<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-faq-cloud-coverage -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# Understanding Defender Experts coverage for servers and cloud workloads

**Applies to:**

- [Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

The following section lists down questions you or your SOC team might have regarding Microsoft Defender Experts coverage for servers and cloud workloads.

| Questions | Answers |
| --- | --- |
| **Can I configure which servers the Defender Experts will cover?** | This service covers **all** your servers in your tenant that have [Defender for Servers](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-servers-overview) protection enabled in Defender for Cloud. |
| **Do the Defender Experts investigate all Defender for Servers alerts?** | The Defender for Servers plan in Defender for Cloud covers multicloud servers, such as Microsoft Azure, Amazon Web Services, and Google Cloud Platform, provided the Microsoft Defender for Endpoint is installed on the servers. All Defender for Servers P1 and P2 alerts \(Detection Source = Microsoft Defender for Servers\) are in scope except for [DNS alerts](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-dns) due to limited data available for investigation. |
| **I only have Microsoft Defender Endpoint. How can I get server coverage?** | If you have servers that have Defender for Endpoint deployed on them with a Microsoft Defender for Endpoint for Server license, you can get the server coverage through the Defender Experts MDR service. The service doesn't cover Microsoft Defender for Cloud workloads. [Learn more](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-prerequisites#product-configuration-and-service-coverage)  <br>  <br>If you want coverage for servers in Defender for Cloud, you need to avail the Microsoft Defender Experts for Servers or Defender Experts Hunting - Servers. |
| **Does Defender Experts MDR Plan 2 cover my Microsoft Defender for Cloud workloads?** | No. Plan 2 extends expert coverage to supported third-party sources, including multicloud sources, that you ingest through Microsoft Sentinel. That telemetry coverage is separate from Microsoft Defender for Cloud workload protection, and neither Defender Experts MDR plan covers Defender for Cloud workloads such as storage, containers, and databases. For expert coverage of servers protected by Defender for Cloud, use Microsoft Defender Experts for Servers or Defender Experts Hunting - Servers. [Learn more about the Defender Experts MDR plans](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-overview) |

### See also

- [General information on Defender Experts MDR service](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-faq)
- [General information on Microsoft Defender Experts Hunting service](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-faq)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
