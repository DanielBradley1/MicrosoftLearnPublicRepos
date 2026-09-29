<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Use shared queries in advanced hunting

[Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) queries can be shared with users in your organization. You can also save queries that only you can access. Community queries on GitHub are available too. With saved queries, you can quickly start hunting for threats. You don't need to write queries from scratch.

The **Queries** tab in advanced hunting lists **Shared queries**, **My queries**, and **Community queries**. Select an arrow to expand a group.

[![Shared queries, My queries, and Community queries in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/advanced-hunting-shared-queries-1.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/advanced-hunting-shared-queries-1.png#lightbox)

## Save, modify, and share a query

You can save a new or existing query so that it is only accessible to you or shared with other users in your organization.

1. Create or modify a query.
2. Click the **Save query** drop-down button and select **Save as**.
3. Enter a name for the query.

   [![The new query that is about to be saved in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/shared-query-2.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/shared-query-2.png#lightbox)
4. Select the folder where you'd like to save the query.

   - **Shared queries** — shared to all users your organization
   - **My queries** — accessible only to you

5. Select **Save**.

## Delete or rename a query

You can rename or delete a saved query at any time.

1. Find the query. Select the three dots next to it.

   [![Rename or delete a query in the Advanced Hunting page in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/advanced-hunting-del-save-query.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/advanced-hunting-del-save-query.png#lightbox)

Caution

Deleting a query removes it permanently. If you want to keep the query, rename it instead.

2. To remove the query, select **Delete** and confirm. To change its name, select **Rename** and enter a new name.

## Create a direct link to a query

To generate a link that opens your query directly in the advanced hunting query editor, finalize your query and select **Share link**.

## Access community queries in the GitHub repo

Microsoft security researchers share hunting queries in a [public GitHub repository](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/Microsoft%20365%20Defender). All queries are reviewed before they're published. To contribute, [join GitHub for free](https://github.com/).

You can also find these queries in the **Community queries** list.

[![Community queries organized by folder in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/advanced-hunting-shared-queries-2.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-shared-queries/advanced-hunting-shared-queries-2.png#lightbox)

Community queries are grouped into folders such as *Campaigns*, *Collection*, and *Defense evasion*. Each query includes in-line comments with more details.

Tip

Microsoft security researchers also share queries that help you find activity linked to emerging threats. Look for these queries in the [threat analytics](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) reports in the Defender portal.

## Related content

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Work with query results](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-results)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
