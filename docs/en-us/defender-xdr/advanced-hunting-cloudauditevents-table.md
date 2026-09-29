<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-cloudauditevents-table -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# CloudAuditEvents

The `CloudAuditEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about cloud audit events for various cloud platforms protected by the organization's [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365#advanced-hunting-in-xdr). Use this reference to construct queries that return information from this table.

This advanced hunting table is populated by records from Microsoft Defender for Cloud. If your organization doesn't have Microsoft Defender for Cloud, queries that use the table aren’t going to work or return any results. For more information about prerequisites in integrating Defender for Cloud with Defender, read [Microsoft Defender integration](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the event was recorded |
| `ReportId` | `string` | Unique identifier for the event |
| `DataSource` | `string` | Data source for the cloud audit events, can be GCP \(for Google Cloud Platform\), AWS \(for Amazon Web Services\), Azure \(for Azure Resource Manager\), Kubernetes Audit \(for Kubernetes\), or other cloud platforms |
| `ActionType` | `string` | Type of activity that triggered the event, can be: Unknown, Create, Read, Update, Delete, Other |
| `OperationName` | `string` | Audit event operation name as it appears in the record, usually includes both resource type and operation |
| `ResourceId` | `string` | Unique identifier of the cloud resource accessed |
| `IPAddress` | `string` | The client IP address used to access the cloud resource or control plane |
| `IsAnonymousProxy` | `boolean` | Indicates whether the IP address belongs to a known anonymous proxy \(1\) or no \(0\) |
| `CountryCode` | `string` | Two-letter code indicating the country where the client IP address is geolocated |
| `City` | `string` | City where the client IP address is geolocated |
| `Isp` | `string` | Internet service provider \(ISP\) associated with the IP address |
| `UserAgent` | `string` | User agent information from the web browser or other client application |
| `RawEventData` | `dynamic` | Full raw event information from the data source in JSON format |
| `AdditionalFields` | `dynamic` | Additional information about the audit event |

## Sample query

To get a sample list of VM creation commands performed in the last seven days:

```kusto
CloudAuditEvents
| where Timestamp > ago(7d)
| where OperationName startswith "Microsoft.Compute/virtualMachines/write"
| extend Status = RawEventData["status"], SubStatus = RawEventData["subStatus"]
| sample 10
```

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
