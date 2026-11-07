<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-04 -->

# Unified cloud.microsoft domain

`cloud.microsoft` is Microsoft's unified, purpose-managed domain for Microsoft 365, Microsoft Copilot, and other Microsoft SaaS experiences in the commercial cloud.

The `cloud.microsoft` domain provides a consistent and durable domain foundation for Microsoft SaaS. Customers can use it to identify Microsoft services, help users recognize official product URLs, configure network policies, and support domain-dependent integrations as Microsoft SaaS products and experiences evolve.

## What is cloud.microsoft?

`cloud.microsoft` is a Microsoft domain dedicated to Microsoft SaaS applications, services, and APIs. It resides under the .microsoft top-level domain, for which Microsoft is the registry operator and sole registrant. Because .microsoft is the top-level domain, `cloud.microsoft` ends there, without a .com, .net, or other suffix.

Every hostname ending in `cloud.microsoft` is within a Microsoft-controlled namespace used for official Microsoft products and services.

Many Microsoft 365 and Microsoft Copilot experiences already use `cloud.microsoft`, with more Microsoft SaaS experiences transitioning to the domain over time.

## Why cloud.microsoft domain unification matters

Domain names affect how people and organizations recognize, trust, configure, secure, and use online services. A consistent domain structure makes Microsoft services easier to recognize and manage as they evolve.

Domain unification provides several benefits:

- **Product identity and trust:** Consistent and recognizable product URLs make it easier for users and organizations to identify official Microsoft services and destinations.
- **Network configuration:** A unified domain structure makes it easier for IT teams to identify Microsoft traffic and apply network policies without maintaining complex configurations for many different product domains.
- **Security and isolation:** Clear domain boundaries help browsers, applications, and security solutions distinguish Microsoft applications and services from third-party sites and other Internet destinations and apply appropriate security policies.
- **Application integration:** A common domain makes it easier for Microsoft applications and services to work together, reducing dependencies on different product-specific domains as experiences become more connected.

Microsoft 365 experiences have historically used many domains for different products and functions. Consolidating Microsoft SaaS experiences under `cloud.microsoft` provides a more consistent experience for users and applications, simplifies configuration for IT and network administrators, and establishes a durable domain foundation as Microsoft services evolve.

## What cloud.microsoft means for enterprise security and networking

Microsoft manages `*.cloud.microsoft` as a purpose-governed namespace for first-party Microsoft SaaS applications, services, and APIs. Services must meet Microsoft requirements for use of the namespace before onboarding and throughout their operation.

Unlike general-purpose Internet domains and cloud hosting platforms, customers and third parties can't use `*.cloud.microsoft` to host their own applications or infrastructure. The namespace excludes customer-managed IaaS and PaaS resources, third-party websites and infrastructure, and third-party executable content. These restrictions give organizations greater confidence that destinations under `*.cloud.microsoft` represent Microsoft-managed services rather than unrelated workloads sharing the same domain.

For Microsoft 365 and Microsoft Copilot, this restriction makes `*.cloud.microsoft` a stable network identifier that IT and security teams can use when configuring network policies. Organizations can apply policies to the namespace instead of evaluating each hostname as an unrelated Internet destination or maintaining application-to-endpoint mappings as Microsoft services evolve.

Allowing connections to `*.cloud.microsoft` provides network reachability to Microsoft services. It doesn't, by itself, give users access to Microsoft services or customer data. Authentication, authorization, and Microsoft 365 security and data-protection controls continue to govern access based on context such as user, device, application, tenant, session, and data.

`*.cloud.microsoft` also uses domain-level security mechanisms including DNSSEC, HTTP Strict Transport Security \(HSTS\) preload, and Certification Authority Authorization \(CAA\). These protections apply consistently across applications and services using the namespace.

## What IT and network teams should do for cloud.microsoft

- **Help users recognize official Microsoft destinations.** Educate users that URLs ending in `cloud.microsoft` are within a Microsoft-controlled namespace used for Microsoft products and services.
- **Allow required connectivity.** Allow `*.cloud.microsoft` and other required [Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide) through firewalls, proxies, and network security solutions so they don't block required service traffic. Don't block individual hostnames within the `cloud.microsoft` namespace.
- **Bypass TLS decryption and inspection.** Microsoft recommends preserving the intended end-to-end TLS connection between clients and `*.cloud.microsoft` destinations. Network solutions that terminate, decrypt, inspect, or modify these TLS connections can affect application availability, performance, interoperability, and supportability. For more information, see [Microsoft 365 TLS decryption guidance](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-intermediation?view=o365-worldwide).
- **Use service-aware controls to enforce organizational policies.** Use Microsoft 365 identity, tenant, application, device, and data-protection controls to govern access to services and customer data. Use `*.cloud.microsoft` as a network policy boundary, not as a substitute for controls that evaluate user, device, application, tenant, session, and data context.
