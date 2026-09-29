<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicefromip-function -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# DeviceFromIP\(\)

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Use the `DeviceFromIP()` function in your [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) queries to quickly obtain the list of devices that have been assigned to a certain IP address at a given point in time.

This function returns a table with the following columns:

| Column | Data type | Description |
| --- | --- | --- |
| `IP` | `string` | IP address |
| `DeviceId` | `string` | Unique identifier for the device in the service |

## Syntax

```kusto
invoke DeviceFromIP()
```

## Arguments

This function is invoked as part of a query.

- **x**—The first parameter is typically already a column in the query. In this case, it's the column named `IP`, the IP address for which you want to see a list of devices that have been assigned to it. It should be a local IP address. External IP addresses aren't supported.
- **y**—A second optional parameter is the `Timestamp`, which instructs the function to obtain the most recent assigned devices from a specific time. If not specified, the function returns the latest available records.

## Example

### Get the latest devices that have been assigned specific IP addresses

```kusto
DeviceNetworkEvents 
| limit 100 
| project IP = LocalIP 
| invoke DeviceFromIP()
```

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
