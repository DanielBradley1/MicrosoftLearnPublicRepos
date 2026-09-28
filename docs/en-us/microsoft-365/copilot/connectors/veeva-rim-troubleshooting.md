<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-rim-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Veeva Vault RIM connector

The Veeva Vault RIM Microsoft 365 Copilot connector allows organizations to index regulatory submissions and compliance documents from Veeva Vault into Microsoft Graph, making them accessible across Microsoft 365 experiences, including Microsoft 365 Copilot and Microsoft Search.

This article provides troubleshooting information for common errors that you might encounter when you deploy the Veeva Vault RIM connector.

## Veeva Vault RIM connector troubleshooting

The following table lists common errors that can occur when you configure the Veeva Vault RIM Microsoft 365 Copilot connector.

| Error | Description | Resolution |
| --- | --- | --- |
| `INVALID_SESSION_ID` | Authentication session expired or invalid. | Reauthenticate with valid credentials. |
| `INSUFFICIENT_ACCESS` | User lacks permissions to access files. | Verify user roles and access control lists \(ACLs\) in Veeva Vault. |
| `API_LIMIT_EXCEEDED` | Too many API requests made in a short period. | Adjust crawl frequency or retry after some time. |
| Missing Properties or Documents | Required metadata properties aren't enabled. | Make sure that metadata properties are enabled in Veeva Vault and test retrieval. |

To view more error types, select the connection and choose **Error details** > **Error code**. For more information, see [Monitor your connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-connector).

## Related content

- [Veeva Vault RIM connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-rim-overview)
- [Deploy the Veeva Vault RIM connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-rim-deployment)
