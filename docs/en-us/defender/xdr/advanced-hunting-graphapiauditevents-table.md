<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-graphapiauditevents-table -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# GraphAPIAuditEvents

The `GraphAPIAuditEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about Microsoft Entra ID API requests made to Microsoft Graph API for resources in the tenant. Use this reference to construct queries that return information from this table.

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `IdentityProvider` | `string` | Identity provider that authenticated the subject of the token |
| `ApiVersion` | `string` | The API version of the event |
| `ApplicationId` | `string` | Unique identifier for the application |
| `ClientRequestId` | `string` | Identifier for the client request sent; if none is available, the operation identifier is used instead |
| `OperationId` | `string` | Identifier for a batch of requests; the same identifier is used for all requests in a batch but if requests are non-batched, the identifier is unique per request |
| `AccountObjectId` | `string` | Unique identifier for the account making the request |
| `Location` | `string` | Name of the region that served the request |
| `RequestDuration` | `string` | Duration of the request in milliseconds |
| `RequestMethod` | `string` | HTTP method of the request |
| `Timestamp` | `datetime` | Date and time when the request was recorded |
| `ResponseStatusCode` | `string` | HTTP response status code for the request |
| `Scopes` | `string` | Scopes in token claims |
| `EntityType` | `string` | Type of object, such as a file, a process, a device, or a user |
| `ReportId` | `string` | Unique identifier for the event |
| `RequestUri` | `string` | Uniform resource identifier \(URI\) of the request |
| `UniqueTokenIdentifier` | `string` | Unique identifier embedded in every access token and ID token that were issued |
| `RequestId` | `string` | Unique identifier of the request |
| `IpAddress` | `string` | IP address from which the request was made |
| `ServicePrincipalId` | `string` | Unique identifier of the service principal that performed the action |
| `TargetWorkload` | `string` | Target workload, such as Microsoft Exchange or Microsoft SharePoint, to which the API call was made |
| `ResponseSize` | `long` | Size of the response in bytes |
| `TenantId` | `string` | Unique identifier representing the organization's instance of Microsoft Entra ID |
| `Type` | `string` | Name of the table |
| `SourceSystem` | `string` | Source system for the record |
| `TimeGenerated` | `datetime` | Date and time when the record was generated |

## Related articles

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
