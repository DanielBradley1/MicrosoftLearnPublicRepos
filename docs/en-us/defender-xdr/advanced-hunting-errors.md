<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-errors -->
<!-- Sitemap-Last-Modified: 2026-05-18 -->

# Handle advanced hunting errors

Advanced hunting displays errors to notify you about syntax mistakes and whenever queries reach [predefined quotas and usage parameters](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-limits). Use the following table to resolve or avoid errors.

| Error type | Cause | Resolution | Error message examples |
| --- | --- | --- | --- |
| Syntax errors | The query contained unrecognized names, including references to nonexistent operators, columns, functions, or tables. | Ensure references to [Kusto operators and functions](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/) are correct. Check [the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables) for the correct advanced hunting columns, functions, and tables. Enclose variable strings in quotes so they're recognized. While writing your queries, use the autocomplete suggestions from IntelliSense. | `A recognition error occurred.` |
| Semantic errors | While the query uses valid operator, column, function, or table names, there were errors in its structure and resulting logic. In some cases, advanced hunting identifies the specific operator that caused the error. | Check for errors in the structure of query. Refer to [Kusto documentation](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/) for guidance. While writing your queries, use the autocomplete suggestions from IntelliSense. | `'project' operator: Failed to resolve scalar expression named 'x'` |
| Timeouts | A query can only run within a [limited period before timing out](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-limits). This error can happen more frequently when running complex queries. | [Optimize the query](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices) | `Query exceeded the timeout period.` |
| CPU throttling | Queries in the same tenant exceeded the [CPU resources](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-limits) that were allocated based on tenant size. | The service checks CPU resource usage every 15 minutes and daily and displays warnings after usage exceeds 10% of the allocated quota. If you reach 100% utilization, the service blocks queries until after the next daily or 15-minute cycle. [Optimize your queries to avoid hitting CPU quotas](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices) | `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Excessive resource consumption | The query consumed excessive amounts of resources and was stopped from completing. In some cases, advanced hunting identifies the specific operator that wasn't optimized. | [Optimize the query](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices) | -`Query stopped due to excessive resource consumption.`  <br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Query size exceeded | An unscoped `search` or `union` query spans all tables in the schema \(both Microsoft Defender and Microsoft Sentinel Log analytics\), which could cause the internal request to exceed Kusto's size limits. This issue is more likely in environments with a large number of tables. | Scope the operator to specific tables using. For example, instead of `search "email"`, use `search in (EmailEvents, EmailAttachmentInfo, IdentityInfo) "email"`. [Optimize your advanced hunting queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices) | `The query cannot run because it exceeds the allowed size limit when processed. ` |
| Unknown errors | The query failed because of an unknown reason. | Try running the query again. Contact Microsoft through the portal if queries continue to return unknown errors. | `An unexpected error occurred during query execution. Please try again in a few minutes.` |

## Related content

- [Advanced hunting best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Quotas and usage parameters](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-limits)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Kusto Query Language overview](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
