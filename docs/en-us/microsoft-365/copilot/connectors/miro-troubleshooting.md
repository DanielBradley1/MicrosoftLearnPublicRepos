<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/miro-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Miro connector

The Miro Microsoft 365 Copilot connector integrates Miro board content into Microsoft 365 so that users can surface boards in Copilot and Microsoft Search. This article provides troubleshooting information for common errors you might encounter when deploying or managing the Miro connector.

To verify Miro configuration details that might help resolve errors, see [Set up the Miro service for Miro connector ingestion](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/miro-admin-setup).

## Miro connector troubleshooting

The following table lists common errors and recommended troubleshooting steps.

| Error | Recommended action |
| --- | --- |
| Required permission scopes are missing. | Ensure that all required scopes are added in the Miro app, including **boards:read**. |
| You don't have the required permission scopes. | Verify that **boards:read** \(Read boards you have access to\) is selected in your app’s configuration. |
| OAuth 2.0 flow failed. | Confirm that the Miro app is configured with valid Client ID and Client secret values, and that the OAuth 2.0 redirect URLs are correct. |
| Authentication error: Incorrect OAuth configuration. | Reopen the Miro app’s **Settings** and confirm that OAuth 2.0 and redirect URLs are correctly set. |
| OAuth 2.0 flow failed due to team admin access. | Ensure that the Miro user associated with the team access token is an active account and has the **team admin** role. |
| Security credentials are expired. | Sign in again with your app’s Client ID and Client secret. Refresh your credentials from the Miro app if needed. |
| Invalid credentials detected. | Verify the Client ID, Client secret, and authorization scopes in the Miro app. Make sure all required scopes are correctly configured. |

## Related content

- [Miro connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/miro-overview)
- [Deploy the Miro connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/miro-deployment)
