<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/freshservice-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Freshservice connector

The Freshservice Microsoft 365 Copilot connector enables your organization to index Freshservice solution article data and make it available to Microsoft 365 Copilot and Microsoft Search. This article provides troubleshooting information for common errors that you might encounter when you deploy the Freshservice connector.

## Freshservice connector troubleshooting

The following table lists common errors and troubleshooting steps for the Freshservice connector.

| Error message or symptom | Possible cause | Troubleshooting steps |
| --- | --- | --- |
| Your security credentials expired for this session. Go back and sign in again with your API key. | Credential information expired. | Create a new API key in the Freshservice API key setting and copy the latest key from the user profile setting page to authenticate. |
| Invalid credentials detected. Check the credentials information. | Common credential error. | Go back to the Freshservice API key setting and verify that the API key is correct. If needed, generate a new API key from your Freshservice user profile settings and update the connector configuration. |

## Related content

- [Freshservice connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/freshservice-overview)
- [Deploy the Freshservice connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/freshservice-deployment)
