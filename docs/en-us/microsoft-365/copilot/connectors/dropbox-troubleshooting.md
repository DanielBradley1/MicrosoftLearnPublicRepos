<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Dropbox connector

The Dropbox connector integrates Dropbox content into Microsoft 365, so Copilot and Microsoft Search can surface files and insights directly within apps such as Teams, Outlook, and SharePoint. This article provides troubleshooting guidance for common issues you might encounter when deploying the Dropbox connector.

To verify Dropbox configuration and assist with troubleshooting, see [Set up the Dropbox service for Dropbox Microsoft 365 Copilot connector ingestion](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-admin-setup).

## Dropbox connector troubleshooting

The following table lists common errors and troubleshooting steps.

| Error | Troubleshooting steps |
| --- | --- |
| Required permission scopes are missing | Make sure that all required scopes are selected in the Dropbox App Console:  <br>**Individual scopes:** files.metadata.read, files.content.read, sharing.read, file\_requests.read  <br>**Team scopes:** team\_info.read, team\_data.member, team\_data.governance.write, team\_data.governance.read, team\_data.content.read, files.team\_metadata.read, members.read, groups.read, events.read |
| OAuth 2.0 flow failed | Verify credential information and confirm that the Dropbox App is configured correctly in the **OAuth 2.0** settings tab. |
| OAuth 2.0 flow failed due to user role | Confirm that the Dropbox user associated with the team access token holds the team admin role and is active. |
| Security credentials expired | Sign in again and refresh credentials. Copy the latest app key and app secret from the Dropbox App Console. |
| Invalid credentials detected | Check credential information and confirm that permission scopes in the Dropbox App Console are correctly configured. |

## Related content

- [Dropbox connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-overview)
- [Deploy the Dropbox connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-deployment)
