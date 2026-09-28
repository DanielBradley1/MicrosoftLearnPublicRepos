<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/azure-file-share-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# Troubleshoot issues with the Azure File Share connector

The Azure File Share Microsoft 365 Copilot connector integrates Azure File Share content into Microsoft 365, so Microsoft 365 Copilot and Microsoft Search experiences can surface relevant files and folders directly in apps like Teams, Outlook, and SharePoint. This article provides troubleshooting information for common errors that you might encounter when you deploy the Azure File Share connector.

## Azure File Share connector troubleshooting

The following table lists common issues and troubleshooting steps.

| Issue | Cause | Resolution |
| --- | --- | --- |
| **Files or folders not appearing in Copilot or Microsoft Search** | The Microsoft Graph Connector Agent account lacks New Technology File System \(NTFS\) read permissions on some directories. | Make sure that the user account used to mount the Azure File Share and run the Microsoft Graph Connector Agent has read access to all directories and files under the source folder paths. |
| **Connector does not index content beyond a certain size** | The connector indexes files up to 100 MB with up to 4 MB of extracted text. Larger files or oversized text extracts are skipped. | Reduce file size or divide content into smaller documents to ensure indexing. |
| **Some file types are not searchable** | Only Office documents, PDFs, text files, and JSON files are supported. Nontext formats \(such as images or videos\) are excluded by default. | Convert nontext content to supported formats if necessary. |
| **Users see fewer results than expected** | The connector enforces NTFS access control lists \(ACLs\), so items not accessible to a specific user don’t appear. | Review NTFS permissions, ensure access alignment with Microsoft Entra ID identities, or adjust access trimming \(if appropriate\). |
| **Slow crawl performance or long delays between updates** | Crawl performance depends on file size, content type, and network conditions of the environment where Microsoft Graph Connector Agent is deployed. | Review network throughput, examine Microsoft Graph Connector Agent host performance, or reduce volume of low-value content. |
| **Agent authentication issues** | The wrong credentials were used for mounting the file share or configuring the agent. | Verify that the same credentials are used for all three operations: mounting the share, running the Microsoft Graph Connector Agent, and configuring the connector in the admin center. |

## Related content

- [Azure File Share connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/azure-file-share-overview)
- [Deploy the Azure File Share connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/azure-file-share-deployment)
