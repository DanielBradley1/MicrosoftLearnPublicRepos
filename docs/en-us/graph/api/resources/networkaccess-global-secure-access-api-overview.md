<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-global-secure-access-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Secure access to cloud, public, and private apps using Microsoft Graph network access APIs \(preview\)

Microsoft Entra Internet Access and Microsoft Entra Private Access comprise Microsoft's Security Service Edge solution and enable organizations to consolidate controls and configure unified identity and network access policies. Microsoft Entra Internet Access secures access to Microsoft 365, SaaS, and public internet apps while protecting users, devices, and data against internet threats. On the other hand, Microsoft Entra Private Access secures access to private apps hosted on-premises or in the cloud.

This article describes the network access APIs in Microsoft Graph that enable the Microsoft Entra Internet Access and Microsoft Entra Private Access services. Global Secure Access is the unifying term for these two services. For more information, see [What is Global Secure Access?](https://learn.microsoft.com/en-us/azure/global-secure-access/overview-what-is-global-secure-access)

## Building blocks of the network access APIs

The network access APIs provide a framework to configure how you want to forward or filter traffic and their associated rules. The following table lists the core entities that make up the network access APIs.

| Entities | Description |
| --- | --- |
| [forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) | Determines how traffic is routed or bypassed through the Global Secure Access services. A forwarding profile is tied to one traffic type that can be Microsoft 365, Internet, or Private traffic. A forwarding profile can then have multiple forwarding policies. For example, the Microsoft 365 forwarding profile has policies for Exchange Online, SharePoint Online, and so on. |
| [forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) | Defines the rules for routing or bypassing specific traffic type through the Global Secure Access services. Each policy is tried to one traffic type that can be Microsoft 365, Internet, or Private traffic. A forwarding policy can have only forwarding policy rules. |
| [forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) | Represents the relationship between a forwarding profile and a forwarding policy, and maintains the current state of the connection. |
| [policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) | Maintains the core definition of a policy ruleset. |
| [remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) | Represents the physical location from where users and devices connect to access the cloud, public, or private apps. Each remote network comprises devices and the connection of devices in a remote network is maintained via customer-premises equipment \(CPE\). |
| [filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) | Groups filtering policies, which are then associated with Conditional Access policies in Microsoft Entra to leverage a rich set of user-context conditions. |
| [filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) | Encapsulates various policies configured by administrators, such as network filtering policies, data loss prevention, and threat protection. |
| [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) | Encapsulates Transport Layer Security inspection configurations that can be linked to filtering profiles in Global Secure Access. See [What is Transport Layer Security inspection?](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-transport-layer-security). |
| [filteringPolicLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) | Represents the relationship between a filtering profile and a filtering policy, and maintains the current state of the connection. |
| [tlsInspectionPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicylink?view=graph-rest-beta) | Represents the relationship between a filtering profile and a TLS inspection policy, and maintains the current state of the connection. |

## Onboard to the service process

To start using the Global Secure Access services and the supporting network access APIs, you must explicitly onboard to the service.

| Operation | Description |
| --- | --- |
| [Onboard tenant](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-onboard?view=graph-rest-beta) | Onboard to the Microsoft Entra Internet Access and Private Access services. |
| [Check status](https://learn.microsoft.com/en-us/graph/api/networkaccess-tenantstatus-get?view=graph-rest-beta) | Check the onboarding status for the tenant. |

## Traffic forwarding profiles and policies

The following APIs allow an admin to manage and configure forwarding profiles. There are three default profiles: Microsoft 365, Private, and Internet. Use the following APIs to manage traffic forwarding profiles and policies.

| Sample operations | Description |
| --- | --- |
| [List forwarding profiles](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingprofiles?view=graph-rest-beta) | List the forwarding profiles configured for the tenant. You can also retrieve the associated policies using the `$expand` query parameter. |
| [Update forwardingProfile](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingprofile-update?view=graph-rest-beta) | Enable or disable a forwarding profile or configure associations such as the remote network. |
| [List forwarding policies](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingpolicies?view=graph-rest-beta) | List the forwarding policies configured for the tenant. You can also retrieve the associated forwarding policy rules using the `$expand` query parameter. |
| [List forwarding policy links](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingprofile-list-policies?view=graph-rest-beta) | List the policy links associated with a forwarding profile. You can also retrieve the associated forwarding policy rules using the `$expand` query parameter. |

## Remote networks

A remote network scenario involves user devices or user-less devices like printers establishing connectivity via customer-premises equipment \(CPE\), also known as device links, at a physical office location.

Use the following APIs to manage the details of a remote network that you've onboarded to the service.

| Sample operations | Description |
| --- | --- |
| [Create a remote network](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-post-remotenetworks?view=graph-rest-beta)  <br>[Create device links for a remote network](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-post-devicelinks?view=graph-rest-beta)  <br>[Create forwarding profiles for a remote network](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-post-forwardingprofiles?view=graph-rest-beta) | Create remote networks and their associated device links and forwarding profiles. |
| [List remote networks](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-list-remotenetworks?view=graph-rest-beta)  <br>[List device links for a remote network](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-list-devicelinks?view=graph-rest-beta)  <br>[List forwarding profiles for a remote network](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-list-forwardingprofiles?view=graph-rest-beta) | List remote networks and their associated device links and forwarding profiles. |

## Access controls

The network access APIs provide a means to manage three kinds of access control settings within your organization: cross-tenant access, conditional access, and forwarding options. These settings ensure secure and efficient network access for devices and users within your tenant.

### Cross-tenant access settings

Cross-tenant access settings involve network packet tagging and the enforcement of tenant restrictions \(TRv2\) policies to help prevent data exfiltration. Use the [crossTenantAccessSettings resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesssettings?view=graph-rest-beta) and its associated APIs to manage cross-tenant access settings.

### Conditional access settings

Conditional access settings in the Global Secure Access services involve enabling or disabling the conditional access signaling for source IP restoration and connectivity. The configuration determines whether the target resource receives the original source IP address of the client or the IP address of the Global Secure Access service.

Use the [conditionalAccessSettings resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesssettings?view=graph-rest-beta) and its associated APIs to manage conditional access settings.

Use the [compliantNetworkNamedLocation resource type](https://learn.microsoft.com/en-us/graph/api/resources/compliantnetworknamedlocation?view=graph-rest-beta) to ensure that users connect from a verified network connectivity model for their specific tenant and are compliant with security policies enforced by administrators.

### Forwarding options

Forwarding options allows administrators to enable or disable the ability to skip DNS lookup at the edge and forward Microsoft 365 traffic directly to Front Door using the client-resolved destination IP. Use the [forwardingOptions resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingoptions?view=graph-rest-beta) and its associated APIs to manage forwarding options.

## Cloud firewall

Cloud firewall in Global Secure Access provides Layer 3 \(Network\) protection by monitoring and controlling all network traffic. Use the cloud firewall APIs to:

- Secure branch traffic acquired using remote networks connectivity for Internet traffic.
- Define firewall policies with granular and prioritized firewall filtering rules to govern outbound traffic, where you can define the source and destination traffic matching conditions and an action in case the traffic matches.
- Create cloud firewall policies with default **allow** action. The default action is applied to all traffic that doesn't match any of the rules in the policy.
- Define a 5-tuple firewall rule with source IP, source port, destination IP, destination port, destination protocol \(TCP and/or UDP\) matching conditions. IP ranges/CIDRs are supported in IP matching conditions.
- Define an action between **allow** and **block**.
- Link a firewall policy for remote networks for Internet traffic to the baseline security profile for policy enforcement.
- Access traffic logs from Entra/GSA portal for cloud firewall.

The following table lists the core entities for managing cloud firewall resources.

| Entities | Description |
| --- | --- |
| [cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) | Represents a cloud firewall policy that provides Layer 3 \(Network\) protection. A cloud firewall policy takes effect once linked to a filtering profile. |
| [cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) | Defines conditions and actions for network traffic filtering within a cloud firewall policy. Each rule specifies matching conditions for source and destination addresses, ports, and protocols. |
| [cloudFirewallPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicylink?view=graph-rest-beta) | Links a cloud firewall policy to a filtering profile. Use the [filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) operations to manage cloud firewall policy links. |

## Logs and monitoring

Monitoring and auditing of events within your environment is crucial for maintaining security, compliance, and operational efficiency. The Global Secure Access events can be accessed through the following resources:

- [directory logs](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta) for changes to the Global Secure Access service
- [sign-in logs](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta) for sign-in events routed through Global Secure Access
- [networkAccessTraffic resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-networkaccesstraffic?view=graph-rest-beta), and [connection resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) and its associated APIs for insights into who is accessing what resources, where they're accessing them from, and what action took place.
- [remoteNetworkHealthEvent resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkhealthevent?view=graph-rest-beta) and its associated APIs to monitor the health and status of IPSec tunnel and the Border Gateway Protocol \(BGP\)
- [reports resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-reports?view=graph-rest-beta) and its associated APIs for summarized network traffic statistics relating to devices, users, transactions and cross-tenant access requests
- [deployment resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta) and its associated APIs for monitoring configuration changes to the service

For more information, see [Global Secure Access logs and monitoring](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-global-secure-access-logs-monitoring).

## Zero Trust

This feature helps organizations to align their tenants with the three guiding principles of a Zero Trust architecture:

- Verify explicitly
- Use least privilege
- Assume breach

To find out more about Zero Trust and other ways to align your organization to the guiding principles, see the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/).

## Related content

- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
