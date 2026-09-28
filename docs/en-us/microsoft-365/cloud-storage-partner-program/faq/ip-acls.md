<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/ip-acls -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# What are the IP ranges and ports used by Microsoft 365 for the web?

Microsoft 365 for the web does not provide IP ranges for partners to use to restrict traffic \(i.e. IP-based ACLs\). Microsoft 365 for the web adds new servers and datacenters regularly and such IP lists will be out of date often. Hosts should use [proof keys](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys) if they wish to verify that requests are coming from Microsoft 365 for the web.

All WOPI communication is done using port 443, the standard HTTPS port.
