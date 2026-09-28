<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/confluence-cloud-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Confluence Cloud Copilot connector

The Confluence Cloud Microsoft 365 Copilot connector integrates Confluence content into Microsoft 365, enabling Copilot and Microsoft Search to surface relevant wiki pages, blogs, and attachments directly within apps like Teams, Outlook, and SharePoint.

The article provides troubleshooting information for common errors that you might encounter when you deploy the Confluence Cloud connector.

To verify Confluence Cloud configuration information to help troubleshoot errors, see [Set up the Confluence Cloud service for connector ingestion](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/confluence-cloud-admin-setup).

## Confluence Cloud connector troubleshooting

You might encounter the following errors when you deploy the Confluence Cloud connector or when the connector indexes data.

| Deployment step | Error or error message | Possible reason |
| :--- | :--- | :--- |
| Connection settings | The request is malformed or incorrect. | Incorrect Confluence site URL. |
| Connection settings | Unable to reach the Confluence cloud service for your Confluence site. | Incorrect Confluence site URL. |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth. |
| Select properties | No error message and no preview results. | Verify that your [CQL query](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/confluence-cloud-admin-setup#set-up-cql-for-advanced-search) is valid. |

## Related content

- [Confluence Cloud connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/confluence-cloud-overview)
- [Deploy the Confluence Cloud connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/confluence-cloud-deployment)
- [Set up the Confluence Cloud service for connector ingestion](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/confluence-cloud-admin-setup)
