<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/bitbucket-pull-request-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the Bitbucket Pull Request connector

The Bitbucket Pull Request Microsoft 365 Copilot connector integrates Bitbucket pull request content into Microsoft 365, so Copilot, Copilot Search, and Microsoft Search can surface relevant pull requests and engineering context directly within Microsoft 365. This article provides troubleshooting information for common errors that you might encounter when you deploy the Bitbucket Pull Request connector.

## Bitbucket Pull Request connector troubleshooting

The following table lists common errors, possible causes, and resolution steps.

| Error message | Possible cause | Resolution |
| --- | --- | --- |
| Data source unreachable | Can't reach Bitbucket API. Network issues or Bitbucket outage. | Check Bitbucket status page. This issue can be transient - retry later. |
| Source throttling crawl | Too many API requests to Bitbucket API \(HTTP 429\). | Automatic retry with exponential backoff \(30s coefficient, rate 2x\). Reduce crawl frequency if persistent. |
| Authentication error | OAuth token is invalid, expired, or missing \(HTTP 401\). App credentials might be incorrect. | Reauthenticate the connection with valid Bitbucket OAuth credentials. Verify OAuth app client ID and secret. |
| Authorization error | Insufficient permissions to access workspace/repository \(HTTP 403\). | Ensure OAuth app has repository, account, pull request scopes. Verify user has read access to repositories. |
| Credentials expired | OAuth refresh token is invalid or expired. | Reauthenticate and obtain new OAuth tokens. Check if OAuth app access was revoked in Bitbucket settings. |
| Identity mapping errors | Bitbucket user identities don't match Microsoft Entra ID properties. | Configure identity mapping using email, sign in, or name. Use regex transformations if direct mapping fails. |
| No searchable items found when previewing content | Preview returned no results. No pull requests \(PR connector\) or no searchable documents \(Knowledge connector\). | **PR:** Ensure at least one pull request exists in selected repositories. **Knowledge:** Ensure at least one .md or .txt file exists in selected repositories. |
| Internal error | Unexpected error during crawl operation. | Check connector logs. Contact support if persistent. |

## Related content

- [Bitbucket Pull Request connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/bitbucket-pull-request-overview)
- [Deploy the Bitbucket Pull Request connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/bitbucket-pull-request-deployment)
