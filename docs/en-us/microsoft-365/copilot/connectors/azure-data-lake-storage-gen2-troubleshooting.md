<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/azure-data-lake-storage-gen2-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# Troubleshoot issues with the Azure Data Lake Storage Gen2 connector

The Azure Data Lake Storage Gen2 Microsoft 365 Copilot connector indexes files stored in [Azure Blob Storage](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction) and [Azure Data Lake Gen 2 Storage](https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) accounts. This article provides troubleshooting information for common errors that you might encounter when you deploy the Azure Data Lake Storage Gen2 connector.

## Azure Data Lake Storage Gen2 connector troubleshooting

The following table lists common errors and possible resolution steps.

| Configuration step | Error message | Possible resolution |
| :--- | :--- | :--- |
| Connection settings | The connection fails even after allowing the public IP address in the ADLS firewall settings. | Allow access to both the virtual network and the IP address \(for disaster recovery purposes\) by using the Azure PowerShell `Add-AzStorageAccountNetworkRule` cmdlet. The Azure portal doesn't provide an option to do that. For syntax and examples, see [Add-AzStorageAccountNetworkRule](https://learn.microsoft.com/en-us/powershell/module/az.storage/add-azstorageaccountnetworkrule). |
| Connection settings | InvalidConfigurationException | Check whether you set up a valid storage for crawls, but later deleted the storage account. |
| Connection settings/crawl | EndpointUnsupportedAccountFeatures \(Error code 7010\) | Your Azure Data Lake Storage Gen2 account has **BlobStorageEvents** or **SoftDelete** enabled. This endpoint doesn't support these features. Disable **BlobStorageEvents** and **SoftDelete** on your storage account, and then retry the connection. Disabling **SoftDelete** can affect data retention and recovery, so only do this action if it's appropriate for your organization's protection requirements. Re-enable **SoftDelete** after troubleshooting if possible. For details, see [How to fix EndpointUnsupportedAccountFeatures](https://learn.microsoft.com/en-us/answers/questions/1853681/how-to-fix-the-problem-endpointunsupportedaccount). |
| Test Connection | Test Connection fails | Ensure the ADLS Gen2–enabled storage account has at least one container with at least one file. A connection error is raised if the content doesn't exist. |

To view more error types, in the Microsoft 365 admin center, select **Connectors**. On the **Your Connections** tab, select the connector and then select the **Error** tab. For more information, see [Monitor errors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/error-responses#monitor-errors).

## Related content

- [Azure Data Lake Storage Gen2 connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/azure-data-lake-storage-gen2-overview)
- [Deploy the Azure Data Lake Storage Gen2 connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/azure-data-lake-storage-gen2-deployment)
