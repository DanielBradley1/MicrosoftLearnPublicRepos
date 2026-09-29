<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-clouddnsevents-table -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# CloudDnsEvents

The `CloudDnsEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about DNS activity events from cloud infrastructure environments. Use this reference to construct queries that return information from this table.

[Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365#advanced-hunting-in-xdr) populates this advanced hunting table with records. If your organization doesn't have Defender for Cloud, queries that use the table won't work or return any results. For more information about prerequisites in integrating Defender for Cloud with Defender, see [Microsoft Defender integration](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365).

For information on other tables in the advanced hunting schema, see [advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the event was recorded |
| `ReportId` | `string` | Unique identifier for the event |
| `ActionType` | `string` | Type of activity that triggered the event |
| `AzureResourceId` | `string` | Unique identifier of the Azure resource associated with the process |
| `AwsResourceName` | `string` | Unique identifier specific to Amazon Web Services devices, containing the Amazon resource name |
| `GcpFullResourceName` | `string` | Unique identifier specific to Google Cloud Platform devices, containing a combination of zone and ID for GCP |
| `KubernetesResource` | `string` | Unique identifier for the Kubernetes resource that includes the namespace, resource type and name |
| `KubernetesNamespace` | `string` | The Kubernetes namespace name |
| `KubernetesPodName` | `string` | The Kubernetes pod name |
| `ContainerName` | `string` | Name of the container in Kubernetes or another runtime environment |
| `ContainerId` | `string` | The container identifier in Kubernetes or another runtime environment |
| `ImageName` | `string` | Container image name or ID |
| `ProcessName` | `string` | The name of the process that initiated the DNS query |
| `ProcessId` | `long` | Process ID that initiated the DNS query |
| `DnsEventType` | `string` | Type of event associated with DNS operation \(for example, query\) |
| `DnsEventSubType` | `string` | Either request or response |
| `DnsQuery` | `string` | The domain that needs to be resolved |
| `DnsQueryTypeName` | `string` | The DNS resource record type name as defined by the Internet Assigned Numbers Authority \(IANA\) |
| `DnsResponseCodeName` | `string` | The DNS response code name as defined by the Internet Assigned Numbers Authority \(IANA\). |
| `DnsNetworkDuration` | `long` | The DNS request duration in milliseconds |
| `TransactionIdHex` | `string` | The DNS unique hex transaction ID |
| `ImageDigest` | `string` | The container's image digest |
| `Region` | `string` | The geographical region where the cluster is located |
| `HostName` | `string` | The node's hostname |
| `AdditionalFields` | `dynamic` | Additional information about the entity or event |

## Sample query

To get the most common DNS queries by a pod in a Kubernetes cluster:

```kusto
CloudDnsEvents
| where AzureResourceId == "<Azure resource ID>"
| where KubernetesNamespace == "<namespace>"
| where KubernetesPodName == "<pod name>"
| where DnsEventSubType == "request"
| summarize count() by DnsQuery
| top 10 by count_ desc
```

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
