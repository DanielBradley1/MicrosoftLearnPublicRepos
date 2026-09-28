<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-promomats-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Veeva PromoMats connector

The Veeva PromoMats Microsoft 365 Copilot connector enables organizations to index and surface approved promotional marketing materials and related compliant content from Veeva Vault PromoMats into the Microsoft 365 ecosystem.

This article provides troubleshooting information for common errors that you might encounter when you deploy the Veeva PromoMats connector.

## Veeva PromoMats connector troubleshooting

The following table lists common errors that can occur when you configure the Veeva PromoMats Microsoft 365 Copilot connector.

| Error | Description | Resolution |
| --- | --- | --- |
| `INVALID_SESSION_ID` | Authentication session expired or invalid. | Reauthenticate with valid credentials. |
| `INSUFFICIENT_ACCESS` | User lacks permissions to access files. | Verify user roles and access control lists \(ACLs\) in Veeva Vault. |
| `API_LIMIT_EXCEEDED` | Too many API requests made in a short period. | Adjust crawl frequency or retry after some time. |
| Missing Properties or Documents | Required metadata properties aren't enabled. | Make sure that metadata properties are enabled in Veeva Vault and test retrieval. |

To view more error types, select the connection and choose **Error details** > **Error code**. For more information, see [Monitor your connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-connector).

## Related content

- [Veeva PromoMats connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-promomats-overview)
- [Deploy the Veeva PromoMats connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-promomats-deployment)
