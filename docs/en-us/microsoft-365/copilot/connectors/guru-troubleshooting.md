<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/guru-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Guru connector

The Guru Microsoft 365 Copilot connector integrates Guru content into Microsoft 365, allowing Copilot and Microsoft Search to surface relevant Guru Cards directly within apps like Teams, Outlook, and SharePoint. This article provides troubleshooting information for common errors that you might encounter when you deploy the Guru connector.

For general deployment steps, see [Deploy the Guru connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/guru-deployment).

## Guru connector troubleshooting

The following table lists common errors and troubleshooting steps.

| Deployment step | Error or error message | Possible reason or troubleshooting |
| --- | --- | --- |
| Connection settings | Can't authenticate with the data source. | Incorrect Guru account or credentials. Verify that the Guru admin account and user token are correct. |
| Select properties | No error message and no preview results. | Verify that your [GQL query](https://developer.getguru.com/docs/guru-query-language) is valid. |
| Permissions sync | Permission changes not reflected immediately. | Updates to users or groups governing access permissions are synced in full crawls only. Incremental crawls don't currently support processing updates to permissions. Wait for the next full crawl or trigger one manually if needed. |
| Identity mapping | Users can't access expected content. | If Guru user email IDs don't match Microsoft Entra ID UPNs, configure identity mapping. See [Map your non-Entra ID identities](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/map-non-entra-id). |
| Content indexing | Some cards are missing from search results. | Only cards outside personal spaces are indexed by default. Review content filters and ensure the Guru Query Language filter is set correctly. |

## Related content

- [Guru connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/guru-overview)
- [Deploy the Guru connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/guru-deployment)
