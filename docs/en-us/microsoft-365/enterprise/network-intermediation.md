<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-intermediation?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# Bypass TLS decryption for Microsoft 365 and Microsoft Copilot

This article explains why Microsoft recommends that you bypass TLS decryption for Microsoft 365 and Microsoft Copilot traffic, and how to configure and verify the bypass. In this guidance, references to Microsoft 365 traffic include Microsoft Copilot traffic unless stated otherwise.

Enterprise environments commonly route Internet connections through proxies and other network security solutions that might terminate and decrypt TLS connections to inspect, filter, or otherwise process traffic. Applying TLS decryption to Microsoft 365 connections can disrupt functionality and user experiences, affect performance and compatibility, and cause application failures. Microsoft doesn't support TLS decryption of Microsoft 365 connections.

## TLS decryption bypass recommendation

- Microsoft recommends bypassing TLS decryption and inspection for Microsoft 365 traffic.
- Configure TLS decryption bypass for the `*.cloud.microsoft` namespace. Microsoft 365 and Microsoft Copilot increasingly use `cloud.microsoft` as a unified domain for application, service, and API experiences, making it a stable network identifier and durable basis for network policy configuration.

For more information about the `cloud.microsoft` domain and its properties, see [Unified `cloud.microsoft` domain](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain?view=o365-worldwide).

Note

Some Microsoft 365 application traffic might still use domains established before the `cloud.microsoft` consolidation. Use [Microsoft 365 Endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-endpoints?view=o365-worldwide) and applicable product documentation to identify additional destinations for TLS decryption bypass configurations.

## TLS decryption bypass and network-path configuration

TLS decryption policy and network-path selection policy are separate configuration decisions. Bypassing TLS decryption doesn't necessarily require removing a proxy, firewall, or network security service from the traffic path. Most network solutions can remain in the path without terminating or decrypting TLS connections to selected destinations.

Evaluate proxy routing, traffic steering, and other network-path decisions separately against [Microsoft 365 network connectivity guidance](#related-content).

## Implement TLS decryption bypass

Create a TLS decryption bypass rule for the `*.cloud.microsoft` namespace, including subdomains. Network products can use different syntax to match a domain and all its subdomains.

Some network products provide preconfigured policies or application definitions for Microsoft 365. If you use a preconfigured policy, verify that it:

- Includes the `cloud.microsoft` domain and applies to all subdomains.
- Reflects current Microsoft 365 endpoint guidance rather than a point-in-time definition of Microsoft 365 traffic.
- Has TLS decryption bypass enabled.
- Has sufficient policy precedence for the bypass to take effect.

Consult your network solution provider's documentation for product-specific configuration instructions.

Apply the bypass consistently across all network paths used by clients to connect to Microsoft 365.

Important

Don't build Microsoft 365 definitions—such as URLs, domains, ports, and protocols—from network traces or point-in-time observations of application traffic and logs. Microsoft 365 URLs, endpoints, and traffic patterns change as the service evolves. Use published Microsoft endpoint and product guidance as the configuration source.

## Verify the configuration

You can verify that TLS decryption bypass takes effect by correlating diagnostic information from the network solution, client-side connection tests, Microsoft 365 network connectivity tools, and Network Insights in the Microsoft 365 admin center. Confirm that connections reach Microsoft 365 without intermediary TLS termination or decryption.

## Use Microsoft 365 controls to implement security and compliance policies

Bypass TLS decryption doesn't mean abandoning security, access, data protection, or compliance requirements for Microsoft 365 scenarios. You can still enforce these requirements through controls that use authoritative Microsoft 365 service context rather than relying on inspection and filtering of decrypted network traffic.

Microsoft 365 controls can evaluate identity, tenant, application, device, session, authorization, and data context. Depending on the required outcome, relevant capabilities are available in Microsoft Entra, Microsoft Intune, Microsoft Purview, Microsoft Defender, and individual Microsoft 365 applications and services.

Define the security or compliance outcome first, identify the service context required to enforce it, and then select the Microsoft 365 control that evaluates that context. This approach keeps the requirement independent of TLS decryption as an implementation mechanism.

Service-aware controls apply policy within Microsoft 365 without inserting a TLS termination and processing stack into client-to-service connections.

## Why Microsoft recommends bypassing TLS decryption for Microsoft 365 and Microsoft Copilot

Microsoft 365 clients and services establish TLS, transport, protocol, and request-flow characteristics directly with each other. TLS decryption replaces this interaction with two separate TLS connections, making connection behavior and application experience dependent on network intermediary processing.

Applying intermediary TLS decryption and network processing to Microsoft 365 connections can affect performance, protocol interoperability, application compatibility, availability, and supportability.

### Performance and responsiveness

TLS decryption and inspection add processing to application connections and requests. This processing often involves buffering or delaying requests and responses before forwarding them. It increases application latency even when network-path latency and available throughput remain unchanged.

Interactive, real-time, and streaming experiences are particularly sensitive to this processing because delays in requests or incremental responses directly affect responsiveness of the application to the end user.

Across reported customer scenarios, Microsoft engineering analysis identified TLS decryption by network security solutions as a cause of substantial increases in latency and materially reduced responsiveness in Microsoft 365 and Microsoft Copilot applications. Bypassing TLS decryption materially improved application performance.

### Protocol interoperability

TLS decryption makes the network intermediary part of protocol handling between Microsoft 365 clients and services. The intermediary processing can constrain, downgrade, or block protocol capabilities instead of the endpoints establishing them directly.

This behavior becomes more consequential as Microsoft 365 uses more advanced protocol, transport, and encryption capabilities, including WebSockets \(WSS\), HTTP/3 \(QUIC\), streaming connections, and newer TLS versions. Intermediary TLS decryption might not preserve the protocol behavior expected by the client and service. This behavior can result in connection fallbacks to a less efficient transport, unavailable functionality, or application timeouts or failures.

### Application compatibility

TLS-decrypting network solutions often use vendor-defined mappings between applications and observable network properties—such as hostnames, URLs, protocols, content types, and request and response patterns—to classify traffic, inspect content, and apply policy actions.

For Microsoft 365, these observable network properties aren't stable application boundaries. They can change as the applications evolve. Additionally, a single Microsoft 365 endpoint can support multiple applications, features, or shared dependencies. Consequently, network processing based on these mappings can misclassify traffic, apply policies incorrectly, block legitimate requests, or make application functionality unavailable.

Compatibility observed at one point in time doesn't establish compatibility with future Microsoft 365 application, service, endpoint, or protocol changes.

### Supportability

TLS decryption inserts customer-managed or third-party processing between Microsoft 365 clients and services. Microsoft doesn't control how intermediary systems terminate TLS connections, classify traffic, or handle and modify application protocols, requests and responses. Microsoft 365 service changes aren't designed or validated against TLS-decrypting network implementations. Consequently, TLS decryption of Microsoft 365 traffic isn't supported.

When investigating Microsoft 365 availability, performance, interoperability, or application issues, Microsoft Support might require the issue to be reproduced without TLS decryption or other intermediary processing.

## Frequently asked questions \(FAQ\)

### My network team reports that Microsoft 365 connections are TLS decrypted and inspected today and they don't see any problems. Does Microsoft still recommend bypassing TLS decryption for Microsoft 365 traffic in my environment?

Yes, Microsoft recommends bypassing TLS decryption for Microsoft 365 traffic regardless of whether the network solution identified a specific impact. The absence of network symptoms doesn't mean that applications are unaffected. Network solution telemetry might not reflect the complete Microsoft 365 user and application experience, limiting network administrators' visibility into application degradation and user impact.

Review application-level signals, user experience data, and Network Insights in the Microsoft 365 admin center to identify existing impact that might not be visible through network and security tools.

Configure TLS decryption bypass in your environment proactively to reduce the risk of future performance, compatibility, and availability issues as Microsoft 365 evolves.

### Does bypassing TLS decryption mean bypassing our proxy, firewall, or network security solution?

Not necessarily. TLS decryption bypass and network-path bypass are separate configuration decisions.

This guidance recommends that a network intermediary not terminate and decrypt Microsoft 365 TLS connections. A proxy, firewall, or network security service can often remain in the traffic path without decrypting those connections.

### Why use \*.cloud.microsoft instead of individual hostnames? Can network policies still target specific products like Microsoft Copilot separately from the rest of Microsoft 365?

Microsoft 365 experiences depend on multiple service endpoints, and a single endpoint can support multiple experiences. Application dependencies, URLs, and hostnames can also change without notice as the service evolves.

`*.cloud.microsoft` provides a Microsoft-defined, stable network identifier for applying TLS decryption bypass across Microsoft 365 and Microsoft Copilot experiences. Individual application-to-hostname mappings aren't a durable basis for such configurations.

Don't infer that an individual product can be isolated from the rest of Microsoft 365 through network configuration. For example, a network policy based on specific destination hostnames and intended to apply only to Microsoft Copilot could also affect shared Microsoft 365 traffic or become incomplete as Microsoft Copilot and its service dependencies change.

When a policy must distinguish based on service-specific properties—for example, application type, tenant identity, user authorization, or data sensitivity—use Microsoft 365 service-aware controls that have the context required to make that distinction.

### Our network security vendor supports TLS decryption of Microsoft 365 traffic. Does Microsoft still recommend bypassing it?

Yes. A network product's ability or vendor support for decrypting Microsoft 365 traffic doesn't change Microsoft's recommendation.

Microsoft's recommendation is based on the Microsoft 365 client-to-service connectivity model and the dependency introduced when an intermediary terminates and processes TLS connections. Network vendor support for this capability doesn't establish compatibility with current or future Microsoft 365 applications, protocols, endpoints, or service changes.

Configure the network solution to bypass TLS decryption in accordance with this guidance.

### Our organization's security or compliance policy requires TLS decryption and inspection. How should we apply this guidance?

Start with the security or compliance outcomes the policy is intended to achieve and determine how those outcomes apply to your Microsoft 365 deployment. Preserve the requirements, but don't assume that TLS decryption is the required implementation mechanism to fulfill those requirements for Microsoft 365 traffic.

Identify each required outcome—for example, controlling access, restricting tenant or application use, preventing data leakage, or monitoring activity. Then use Microsoft 365 service-aware controls that evaluate the relevant identity, tenant, application, device, authorization, and data context.

Relevant capabilities are available in Microsoft Entra, Microsoft Intune, Microsoft Purview, Microsoft Defender, and individual Microsoft 365 applications and services.

## Related content

- [Unified cloud.microsoft Domain](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain?view=o365-worldwide).
- [Microsoft 365 Endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-endpoints?view=o365-worldwide).
- [Microsoft 365 Network Connectivity Principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles?view=o365-worldwide).
- [Microsoft 365 Network Insights](https://learn.microsoft.com/en-us/microsoft-365/enterprise/office-365-network-mac-perf-insights?view=o365-worldwide).
- [Microsoft 365 Network Connectivity Test](https://connectivity.m365.cloud.microsoft).
