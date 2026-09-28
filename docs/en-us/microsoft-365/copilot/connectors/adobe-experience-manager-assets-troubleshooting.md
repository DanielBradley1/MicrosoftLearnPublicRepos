<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/adobe-experience-manager-assets-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-05-20 -->

# Troubleshoot issues with the Adobe Experience Manager Assets connector

The Adobe Experience Manager Assets Microsoft 365 Copilot connector integrates Adobe Experience Manager \(AEM\) Assets content into the Microsoft 365 ecosystem. This integration allows Copilot and Microsoft Search experiences to surface published assets.

This article provides troubleshooting information for common errors that you might encounter when you deploy the connector.

## Adobe Experience Manager Assets connector troubleshooting

You might encounter the following errors when you deploy the connector or when the connector indexes data.

| Deployment step | Error or error message | Possible reason |
| --- | --- | --- |
| Connection settings | Can't authenticate with the data source. | Verify that your Adobe Experience Cloud instance author environment and publish environment URLs are correct and verify that your credentials are valid. |
| Connection settings | Don't have permission to access this data source. | To connect to Adobe Experience Manager Assets and allow the connector to update published assets regularly, you need a technical account with credentials to access published assets and metadata. The technical account is a secure, service-based account for external access. For details, see [Generate access tokens for server-side APIs](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis). |

## Related content

- [Adobe Experience Manager Assets connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/adobe-experience-manager-assets-overview)
- [Deploy the Adobe Experience Manager Assets connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/adobe-experience-manager-assets-deployment)
