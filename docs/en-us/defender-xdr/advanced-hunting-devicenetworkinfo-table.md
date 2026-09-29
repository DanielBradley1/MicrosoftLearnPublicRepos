<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicenetworkinfo-table -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# DeviceNetworkInfo

The `DeviceNetworkInfo` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about networking configuration of machines, including network adapters, IP and MAC addresses, and connected networks or domains. Use this reference to construct queries that return information from this table.

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the event was recorded |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `NetworkAdapterName` | `string` | Name of the network adapter |
| `MacAddress` | `string` | MAC address of the network adapter |
| `NetworkAdapterType` | `string` | Network adapter type. For the possible values, refer to [this enumeration](https://learn.microsoft.com/en-us/dotnet/api/system.net.networkinformation.networkinterfacetype). |
| `NetworkAdapterStatus` | `string` | Operational status of the network adapter. For the possible values, refer to [this enumeration](https://learn.microsoft.com/en-us/dotnet/api/system.net.networkinformation.operationalstatus). |
| `TunnelType` | `string` | Tunneling protocol, if the interface is used for this purpose, for example 6to4, Teredo, ISATAP, PPTP, SSTP, and SSH |
| `ConnectedNetworks` | `string` | Networks that the adapter is connected to. Each JSON element in the array contains the network name, category \(public, private or domain\), a description, and a flag indicating if it's connected publicly to the internet. |
| `DnsAddresses` | `string` | DNS server addresses in JSON array format |
| `IPv4Dhcp` | `string` | IPv4 address of DHCP server |
| `IPv6Dhcp` | `string` | IPv6 address of DHCP server |
| `DefaultGateways` | `string` | Default gateway addresses in JSON array format |
| `IPAddresses` | `string` | JSON array containing all the IP addresses assigned to the adapter, along with their respective subnet prefix and IP address space, such as public, private, or link-local |
| `ReportId` | `long` | Event identifier based on a repeating counter. To identify unique events, this column must be used in conjunction with the DeviceName and Timestamp columns. |
| `NetworkAdapterVendor` | `string` | Name of the manufacturer or vendor of the network adapter |
| `OnboardingStatus` | `string` | Indicates whether the device is currently onboarded to Microsoft Defender for Endpoint or if the device is not supported |
| `NetworkAdapterDnsSuffix` | `string` | Domain suffix assigned to the device’s network adapter, indicating the network environment the network adapter is connected to |

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
