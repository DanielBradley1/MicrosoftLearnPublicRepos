<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/shortcut-story-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Shortcut Story connector

The Shortcut Story Microsoft 365 Copilot connector empowers your organization to index and search Shortcut stories across your enterprise. This article provides troubleshooting information for common errors that you might encounter when you deploy the Shortcut Story connector. Use these steps to resolve issues and ensure successful indexing of Shortcut stories.

## Shortcut Story connector troubleshooting

The following table lists common errors and troubleshooting steps.

| Error | Possible cause | Resolution |
| --- | --- | --- |
| Authentication failed | Invalid or missing API token | Confirm that the API token was generated in Shortcut under **Settings > My Account > API Token**. Ensure the token is active and entered correctly in the Microsoft 365 admin center. |
| Connector not indexing stories | Incorrect instance URL or network connectivity issues | Verify that the instance URL is `https://api.app.shortcut.com`. Check network connectivity and firewall settings to allow access to Shortcut API endpoints. |
| No items indexed after initial crawl | Crawl frequency or permissions misconfigured | Confirm that incremental crawl is set to run every 15 minutes and full crawl every day. Ensure access permissions are configured so only users with access to Shortcut content can view indexed stories. |
| Identity mapping errors | Entra ID mapping incomplete | Review identity mapping settings in **Custom setup**. Ensure Shortcut identities are mapped to Microsoft Entra IDs. |
| Data mismatch in Copilot responses | Schema or property configuration incorrect | Check property schema settings in **Manage properties**. Verify that key fields like `Name`, `Description`, and `Url` are marked as searchable and retrievable. |

## Related content

- [Shortcut Story connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/shortcut-story-overview)
- [Deploy the Shortcut Story connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/shortcut-story-deployment)
