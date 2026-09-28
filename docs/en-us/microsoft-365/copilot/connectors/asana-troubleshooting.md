<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/asana-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Asana Copilot connector

The Asana Microsoft 365 Copilot connector enables users to surface Asana tasks in Microsoft 365 apps such as Teams, Outlook, and SharePoint using Copilot, Copilot Search, and Microsoft Search. This article provides troubleshooting information for common errors that you might encounter when you deploy the Asana connector.

## Asana connector troubleshooting

The following table lists common errors and recommended troubleshooting steps.

| Error or issue | Possible cause | Recommended action |
| --- | --- | --- |
| **Tasks not appearing in Copilot or search** | Permissions mismatch between Asana and Microsoft Entra ID | Verify that identity mapping is correctly configured. Make sure that Asana user emails match Microsoft Entra ID user principal names \(UPNs\). |
| **Connector fails to authenticate** | Invalid or expired OAuth token | Reauthenticate the connector using a valid OAuth 2.0 token. Consider switching to API token for testing. |
| **Incomplete task data indexed** | Connector doesn't support custom fields | This is a known limitation. Ensure that required data is included in supported fields. |
| **Permission changes not reflected immediately** | Connector sync delay | Wait for the next scheduled crawl. Full crawls occur every 24 hours; incremental crawls every 15 minutes. |
| **Connector setup fails in admin center** | Incorrect workspace URL or missing API access | Confirm that the Asana workspace URL is correct and that API access is enabled for the workspace. |
| **Tasks from archived projects are indexed** | Default content settings include all tasks | Customize content settings to exclude archived projects or completed tasks. |

## Related content

- [Asana connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/asana-overview)
- [Deploy the Asana connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/asana-deployment)
