<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-cloudkeyvaultevents-table -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# CloudKeyVaultEvents \(Preview\)

The `CloudKeyVaultEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about operations performed against Azure Key Vault resources. Use this reference and the sample queries to investigate Key Vault access, caller identities, and operation results in Microsoft Defender XDR.

Important

Some information relates to a prereleased product that might be substantially modified before commercial release. Microsoft makes no warranties, express or implied, with respect to this information.

This advanced hunting table is populated by records from [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365#advanced-hunting-in-xdr). If your organization doesn't have Microsoft Defender for Cloud, queries that use the table won't work or return any results. [Microsoft Defender for Key Vault](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-key-vault-introduction) protection must be enabled for the relevant Azure subscriptions. For more information about prerequisites for integrating Defender for Cloud with Microsoft Defender XDR, see [Microsoft Defender XDR integration](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-integration-365).

For information on other tables in the advanced hunting schema, see the [advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the record was generated. |
| `ReportId` | `string` | GUID that identifies the record in this table. |
| `DataSource` | `string` | Source of the Key Vault logs. |
| `SubscriptionId` | `string` | Unique identifier of the Azure subscription. |
| `AzureResourceId` | `string` | Azure resource ID of the key vault. |
| `Location` | `string` | Azure region where the key vault is located. |
| `ActivityName` | `string` | Name of the Key Vault operation performed. |
| `IPAddress` | `string` | IP address from which the key vault was accessed. |
| `HttpStatusCode` | `int` | HTTP status code returned by the Key Vault operation. |
| `ResultSignature` | `string` | Result signature of the Key Vault operation. |
| `AccountTenantId` | `string` | Unique identifier of the Microsoft Entra tenant associated with the accessing account. |
| `AccountApplicationId` | `string` | Application ID associated with the Key Vault access. |
| `AccountType` | `string` | Type of account used to access the key vault. |
| `AccountObjectId` | `string` | Object ID of the identity accessing the key vault. |
| `AccountUpn` | `string` | User principal name of the user accessing the key vault. |
| `RequestUri` | `string` | URI of the Key Vault request. |
| `VaultName` | `string` | Name of the key vault. |
| `UserAgentHeader` | `string` | User-agent string from the HTTP request. |
| `AdditionalFields` | `dynamic` | Additional information about the event in JSON format. |

## Sample queries

These queries are investigation examples, not validated detection rules. A failed request or a high operation count doesn't by itself establish malicious activity.

### Review recent Key Vault operations

List the 100 most recent operations from the past day, including the accessing identity and operation result.

```kusto
CloudKeyVaultEvents
| where Timestamp > ago(1d)
| top 100 by Timestamp desc
| project Timestamp, ReportId, SubscriptionId, AzureResourceId,
    VaultName, ActivityName, AccountType, AccountObjectId,
    AccountUpn, AccountApplicationId, IPAddress,
    HttpStatusCode, ResultSignature, RequestUri
```

### Discover operation names in your environment

Identify the operation names present in the data before creating operation-specific queries.

```kusto
CloudKeyVaultEvents
| where Timestamp > ago(7d)
| summarize Operations = count() by ActivityName
| order by Operations desc
```

### Investigate unauthorized and forbidden requests

Review operations that returned HTTP status code `401` \(Unauthorized\) or `403` \(Forbidden\). Use the caller identity, source IP address, and request URI to investigate whether the failures are expected.

```kusto
CloudKeyVaultEvents
| where Timestamp > ago(7d)
| where HttpStatusCode in (401, 403)
| project Timestamp, ReportId, AzureResourceId, VaultName,
    ActivityName, AccountObjectId, AccountUpn,
    AccountApplicationId, IPAddress, HttpStatusCode,
    ResultSignature, RequestUri
| order by Timestamp desc
```

### Find callers with frequent request failures

Find caller and vault combinations with more than 20 requests returning HTTP `4xx` or `5xx` status codes in an hour. Adjust the illustrative threshold to match normal activity in your environment. Group by the resource ID as well as the vault name to distinguish resources across subscriptions.

```kusto
CloudKeyVaultEvents
| where Timestamp > ago(7d)
| where HttpStatusCode between (400 .. 599)
| summarize FailedOperations = count(),
    Activities = make_set(ActivityName, 50)
    by bin(Timestamp, 1h), AzureResourceId, VaultName,
    AccountObjectId, AccountApplicationId, IPAddress
| where FailedOperations > 20
| order by FailedOperations desc
```

### Summarize successful operations by identity and vault

Review successful requests by caller and vault. HTTP `2xx` responses are treated as successful requests in this example.

```kusto
CloudKeyVaultEvents
| where Timestamp > ago(7d)
| where HttpStatusCode between (200 .. 299)
| summarize SuccessfulOperations = count(),
    Activities = make_set(ActivityName, 50),
    SourceIPs = make_set(IPAddress, 50)
    by AzureResourceId, VaultName, AccountObjectId,
    AccountUpn, AccountApplicationId
| order by SuccessfulOperations desc
```

## Related content

- [Advanced hunting schema reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Microsoft Defender for Key Vault](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-key-vault-introduction)
- [Advanced hunting query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Create custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules)
