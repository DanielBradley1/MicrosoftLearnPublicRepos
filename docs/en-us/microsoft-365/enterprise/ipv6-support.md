<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/ipv6-support?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# IPv6 support in Microsoft 365 services

With the growing adoption and support of IPv6 across enterprise networks, service providers, and devices, many customers are wondering if their users can continue to access Microsoft 365 services from IPv6 clients and IPv6 networks. Microsoft 365 services can be successfully used from both IPv6 dual stack and IPv6-only devices \(IPv6-only devices require translation technologies such as DNS64 or NAT64\). In fact, we have an increasing number of customers, from consumers to large enterprises, who are moving towards greater adoption of IPv6. For most customers, IPv4 won't completely disappear from their digital landscape, so we aren't planning to require IPv6 or to deprioritize IPv4 in any Microsoft 365 features or services.

One of our key priorities with Microsoft 365 is to ensure seamless customer and user experiences over the Internet from any location, from any device. This includes access to Microsoft 365 from customer devices that are using IPv6 in the dual stack configuration as well as transitioning to IPv6-only client deployments. In most cases, when you follow a standard Internet-based model of connecting to Microsoft 365 as described in [Microsoft 365 network connectivity principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles?view=o365-worldwide), [Microsoft 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide), and [Microsoft 365 network planning best practices](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-and-migration-planning?view=o365-worldwide#best-practices-for-network-planning-and-improving-migration-performance-for-microsoft-365), IPv6 transitions won't be disruptive to your user experience.

Many Microsoft 365 services already provide native IPv6 support today and can be accessed directly from IPv6 dual stack and IPv6-only clients. Microsoft 365 also allows access through conventional IPv6 to IPv4 translation technologies \(such as base 64 proxies or DNS64/NAT64\) commonly used by customers and network solution providers to connect to IPv4 Internet resources.

As with any SaaS service and the Internet overall, the scope of natively IPv6 enabled Microsoft 365 interfaces, features, and APIs expands continuously and without direct customer action or control. If you're running IPv6 or IPv6-only services on your networks that need access to Microsoft 365 and the Internet, it's recommended that you include dynamic IPv6/IPv4 transitional mechanisms such as DNS64/NAT64 to ensure end-to-end IPv6 connectivity to Microsoft 365 without any further network reconfigurations.

Most of Microsoft 365 services have been or will be enabled with IPv6 capabilities transparently for end users and IT admins. Some Microsoft 365 scenarios \(such as anonymous inbound e-mail\) do have special requirements and considerations for use in conjunction with IPv6. For more details about scenario specific IPv6 requirements and considerations, contact your Microsoft account team or Microsoft support.

## Related content

- [Microsoft 365 Network Connectivity Overview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-networking-overview?view=o365-worldwide)
- [Managing Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints?view=o365-worldwide)
- [Microsoft 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide)
- [Microsoft 365 IP Address and URL Web service](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-ip-web-service?view=o365-worldwide)
- [Assessing Microsoft 365 network connectivity](https://learn.microsoft.com/en-us/microsoft-365/enterprise/assessing-network-connectivity?view=o365-worldwide)
- [Network planning and performance tuning for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance?view=o365-worldwide)
- [Microsoft 365 performance tuning using baselines and performance history](https://learn.microsoft.com/en-us/microsoft-365/enterprise/performance-tuning-using-baselines-and-history?view=o365-worldwide)
- [Performance troubleshooting plan for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/performance-troubleshooting-plan?view=o365-worldwide)
- [Content Delivery Networks](https://learn.microsoft.com/en-us/microsoft-365/enterprise/content-delivery-networks?view=o365-worldwide)
- [Microsoft 365 connectivity test](https://connectivity.office.com/)
- [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
- [Microsoft 365 Networking blog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
