<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-cloudpolicyenforcementevents-table -->
<!-- Sitemap-Last-Modified: 2026-03-30 -->

# CloudPolicyEnforcementEvents \(Preview\)

The `CloudPolicyEnforcementEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains policy enforcement evaluation decisions and metadata of security gating events for various cloud platforms protected by the organization's [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365#advanced-hunting-in-xdr). Use this reference to construct queries that return information from this table.

Important

Some information relates to prereleased product, which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Defender for Cloud populates this advanced hunting table with records. If your organization doesn't have Microsoft Defender for Cloud, queries that use the table won't work or return any results. For more information about prerequisites in integrating Defender for Cloud with Defender, see [Microsoft Defender XDR integration](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365).

For information on other tables in the advanced hunting schema, see the [advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the record was generated |
| `ReportId` | `string` | Unique identifier for the event |
| `DataSource` | `string` | Data source of the cloud events; possible values: Google Kubernetes Engine, Elastic Kubernetes Service, or Azure Kubernetes Service |
| `SubscriptionId` | `string` | Unique identifier assigned to the Azure subscription |
| `ActionType` | `string` | Type of activity that resulted from the policy enforcement operation; possible values: Audit, Deny, or Allow |
| `AzureResourceId` | `string` | Unique identifier of the Azure resource associated with the event |
| `AwsResourceName` | `string` | Unique identifier specific to Amazon Web Services devices, containing the Amazon resource name |
| `GcpFullResourceName` | `string` | Unique identifier specific to Google Cloud Platform devices, containing a combination of zone and ID for GCP |
| `Region` | `string` | The region associated with the Kubernetes cluster |
| `ResourceKind` | `string` | Type or kind of Kubernetes resource created or managed \(for example, pod or deployment\) |
| `ResourceName` | `string` | Name of the Kubernetes resource |
| `KubernetesNamespace` | `string` | The Kubernetes namespace name |
| `Reason` | `string` | Information explaining the action result |
| `AdditionalFields` | `string` | Additional information about the entity or event |

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
