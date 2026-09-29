<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-exposuregraphnodes-table -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# ExposureGraphNodes

**Applies to:**

- Microsoft Defender XDR
- Microsoft Security Exposure Management \(public preview\)

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `ExposureGraphNodes` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains organizational entities and their properties. These include entities like devices, identities, user groups, and cloud assets such as virtual machines \(VMs\), storage, and containers. Each node corresponds to an individual entity and encapsulates information about its characteristics, attributes, and security related insights within the organizational structure. Use this reference to construct queries that return information from this table.

This advanced hunting table is populated by records from various Microsoft Defender services, including Defender for Endpoint, Defender for Identity, Defender for Cloud, Entra ID, and others. The table also gets populated by third-party data through the various Security Exposure Management data connectors. The more security products you deploy, the richer the graph becomes with more meaningful data. If your organization hasn't deployed any service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy services in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `NodeId` | `string` | Unique node identifier |
| `NodeLabel` | `string` | Node label |
| `NodeName` | `string` | Node display name |
| `Categories` | `dynamic` | Categories of the node in JSON format |
| `NodeProperties` | `dynamic` | Properties of the node, including insights related to the resource, such as whether the resource is exposed to the internet, or vulnerable to remote code execution. Values are JSON formatted raw data \(unstructured\). |
| `EntityIds` | `dynamic` | All known node identifiers in JSON format |

## Related articles

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Query the enterprise exposure graph](https://learn.microsoft.com/en-us/security-exposure-management/query-enterprise-exposure-graph)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
