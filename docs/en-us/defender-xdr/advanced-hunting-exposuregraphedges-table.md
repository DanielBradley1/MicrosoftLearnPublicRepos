<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-exposuregraphedges-table -->
<!-- Sitemap-Last-Modified: 2025-06-20 -->

# ExposureGraphEdges

**Applies to:**

- Microsoft Defender XDR
- Microsoft Security Exposure Management \(public preview\)

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `ExposureGraphEdges` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema provides visibility into relationships between entities and assets in the enterprise exposure graph. This visibility can help uncover critical organizational assets and explore entity relationships and attack paths. Use this reference to construct queries that return information from this table.

This advanced hunting table is populated by records from various Microsoft Defender services, including Defender for Endpoint, Defender for Identity, Defender for Cloud, Entra ID, and others. The table also gets populated by third-party data through the various Security Exposure Management data connectors. The more security products you deploy, the richer the graph becomes with more meaningful data. If your organization hasn't deployed any service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy services in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `EdgeId` | `string` | Unique identifier for the relationship/edge |
| `EdgeLabel` | `string` | The edge label like "routes traffic to" |
| `SourceNodeId` | `string` | Node ID of the edge's source |
| `SourceNodeName` | `string` | Source node display name |
| `SourceNodeLabel` | `string` | Source node label |
| `SourceNodeCategories` | `dynamic` | Categories list of the source node in JSON format |
| `TargetNodeId` | `string` | Node ID of the edge's target |
| `TargetNodeName` | `string` | Display name of the target node |
| `TargetNodeLabel` | `string` | Target node label |
| `TargetNodeCategories` | `dynamic` | The categories list of the target node in JSON format |
| `EdgeProperties` | `dynamic` | Optional data relevant for the relationship between the nodes in JSON format |

## Related articles

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Query the enterprise exposure graph](https://learn.microsoft.com/en-us/security-exposure-management/query-enterprise-exposure-graph)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
