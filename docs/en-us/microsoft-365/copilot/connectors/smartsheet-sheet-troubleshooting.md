<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/smartsheet-sheet-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Smartsheet Sheet connector

The Smartsheet Sheet Microsoft 365 Copilot connector indexes Smartsheet content so users can retrieve and analyze it in Microsoft 365 Copilot and Microsoft Search experiences. This article provides troubleshooting information for common issues you might encounter.

## Smartsheet Sheet connector troubleshooting

If you encounter issues with the connector, consider the following areas:

- **Authentication errors**: Make sure that the API Access Token is valid and belongs to a System Admin user.
- **Connectivity**: Verify that you selected the correct Smartsheet instance region \(`https://api.smartsheet.com` or `https://api.smartsheet.eu`\).
- **Permissions**: If users can't see content they expect, check the identity mapping settings. Make sure that Smartsheet email addresses match Microsoft Entra ID user principal names \(UPNs\) or that a correct custom mapping rule is in place.

For more information about index browser search and Smartsheet IDs, see [How to get Smartsheet IDs](https://help.smartsheet.com/articles/2482711-get-smartsheet-ids) in the Smartsheet Learning Center.

## Related content

- [Smartsheet Sheet connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/smartsheet-sheet-overview)
- [Deploy the Smartsheet Sheet connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/smartsheet-sheet-deployment)
- [Manage your connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-connector)
