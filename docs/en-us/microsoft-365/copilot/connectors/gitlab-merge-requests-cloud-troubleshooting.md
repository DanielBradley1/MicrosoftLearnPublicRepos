<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/gitlab-merge-requests-cloud-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Troubleshoot issues with the GitLab Merge Requests Cloud connector

The GitLab Merge Requests Cloud Microsoft 365 Copilot connector allows your organization to index merge request data stored in GitLab and make it available across Microsoft 365 Copilot and Microsoft Search experiences. This article provides troubleshooting guidance for common issues you might encounter when you deploy or manage the GitLab Merge Requests Cloud connector. These issues typically relate to authentication, permissions, configuration, ingestion, and sync behavior.

## GitLab Merge Requests Cloud connector troubleshooting

The following table lists common issues and possible resolutions.

| Issue | Cause | Resolution |
| --- | --- | --- |
| Authentication fails during OAuth authorization | Incorrect client ID or client secret; missing OAuth scopes | Confirm the client ID and client secret match the values generated in GitLab. Ensure the app includes the **read\_api**, **read\_repository**, and **read\_user** scopes. |
| OAuth callback error appears after authorization | Incorrect redirect URL in GitLab OAuth app settings | Verify that GitLab is configured with the correct redirect URL:  <br>**Enterprise**: `https://gcs.office.com/v1.0/admin/oauth/callback`  <br>**Government**: `https://gcsgcc.office.com/v1.0/admin/oauth/callback`. |
| GitLab data doesn't appear in Microsoft 365 Copilot or Microsoft Search | Identity mapping unsuccessful or GitLab identities don't match Microsoft Entra ID fields | Review identity mapping settings \(Email, sign in, or name\). If identity formats differ, use regex to transform values for correct mapping. |
| Connector deploys successfully but no items are indexed | Authentication account lacks required GitLab permissions | Ensure the authentication account has access to repositories, issues, merge requests, knowledge files, and wiki pages. |
| Only partial data appears in search or Copilot | Property mapping doesn't include needed metadata | Review **Manage properties** in Custom setup. Add or adjust property schema settings \(searchable, queryable, retrievable, refinable\). |
| Ingestion is slow or incomplete | GitLab API rate limits or large repository volumes | Review GitLab rate limits. Consider adjusting incremental or full crawl intervals to balance load and freshness. |
| Incremental sync doesn't pick up recent updates | Sync intervals set too infrequently or metadata missing required timestamps | Confirm incremental sync is set to every 15 minutes or adjust as needed. Ensure merge requests include updated timestamp metadata. |
| Full sync takes longer than expected | High data volume or environment load | Allow extra processing time for large GitLab organizations. Adjust full crawl frequency if needed. |
| Users can't see expected merge requests in Copilot | Access permission setting excludes them | If necessary, update Access permissions from **Only people with access to this data source** to **Everyone**, based on your organization's security model. |

## Related content

- [GitLab Merge Requests Cloud connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/gitlab-merge-requests-cloud-overview)
- [Deploy the GitLab Merge Requests Cloud connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/gitlab-merge-requests-cloud-deployment)
