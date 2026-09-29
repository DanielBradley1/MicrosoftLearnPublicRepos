<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-assignedipaddresses-function -->
<!-- Sitemap-Last-Modified: 2025-03-28 -->

# AssignedIPAddresses\(\)

Use the `AssignedIPAddresses()` function in your [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) queries to quickly obtain the latest IP addresses that have been assigned to a device. If you specify a timestamp argument, this function obtains the most recent IP addresses at the specified time.

This function returns a table with the following columns:

| Column | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Latest time when the device was observed using the IP address |
| `IPAddress` | `string` | IP address used by the device |
| `IPType` | `string` | Indicates whether the IP address is a public or private address |
| `NetworkAdapterType` | `int` | Network adapter type used by the device that has been assigned the IP address. For the possible values, refer to [this enumeration](https://learn.microsoft.com/en-us/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `ConnectedNetworks` | `int` | Networks that the adapter with the assigned IP address is connected to. Each JSON array contains the network name, category \(public, private, or domain\), a description, and a flag indicating if it's connected publicly to the internet |

## Syntax

```kusto
AssignedIPAddresses(x, y)
```

## Arguments

- **x**—`DeviceId` or `DeviceName` value identifying the device
- **y**—`Timestamp` \(datetime\) value instructing the function to obtain the most recent assigned IP addresses from a specific time. If not specified, the function returns the latest IP addresses.

## Examples

### Get the list of IP addresses used by a device 24 hours ago

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### Get IP addresses used by a device and find devices communicating with it

This query uses the `AssignedIPAddresses()` function to get assigned IP addresses for the device \(`example-device-name`\) on or before a specific date \(`example-date`\). It then uses the IP addresses to find connections to the device initiated by other devices.

```kusto
let Date = datetime(example-date);
let DeviceName = "example-device-name";
// List IP addresses used on or before the specified date
AssignedIPAddresses(DeviceName, Date)
| project DeviceName, IPAddress, AssignedTime = Timestamp 
// Get all network events on devices with the assigned IP addresses as the destination addresses
| join kind=inner DeviceNetworkEvents on $left.IPAddress == $right.RemoteIP
// Get only network events around the time the IP address was assigned
| where Timestamp between ((AssignedTime - 1h) .. (AssignedTime + 1h))
```

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
