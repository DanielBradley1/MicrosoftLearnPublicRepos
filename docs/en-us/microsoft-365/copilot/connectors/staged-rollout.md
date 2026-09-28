<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/staged-rollout -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Staged rollout for connectors

Staged rollout of Microsoft 365 Copilot connectors allows you to gradually introduce a connector to a select group of users in your production environment. You can use it to deploy an existing or new connection to a limited set of users, monitor the performance, and adjust settings as needed. You can expand or reduce the scope of the rollout at any time. When you're ready, you can end the staged rollout and deploy the connection to the entire organization \(or to all applicable users\).

For information about how to set up Copilot connectors, see [Deploy Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview).

This article describes how to apply staged rollout to a Copilot connector and how to edit staged rollout settings.

Important

- Staged rollout settings are applicable to all Search and Copilot experiences.
- You must be an AI administrator to access this feature.

## Apply staged rollout to a new connection

Complete the following steps to apply a staged rollout to a new connection:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Copilot** > **Connectors**.
2. On the **Gallery** tab, choose the connector that you want to deploy.
3. Configure the connection settings as described in the [Deployment overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview) article.
4. Select the toggle next to **Rollout to limited audience**.
5. Add the users or security groups that you want to have access to the connector. You can add up to 100 users and 15 Microsoft 365 groups.
6. Choose **Create** to create the connection. When the rollout finishes, only the users and groups you specified see connector data in results, depending on their permissions.

[![Screenshot of the Rollout to a limited audience toggle on the connector setup page.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/staged-rollout/staged-rollout.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/staged-rollout/staged-rollout.png#lightbox)

## Modify staged rollout

To modify the staged rollout settings for a connector:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Copilot** > **Connectors** > **Your Connections**.
2. Find the connector that you want to modify.
3. In the **Staged Rollout** column, next to **Staged**, choose **Edit**.
4. Add or remove users and groups from the staged rollout, and choose **Save**.

[![Screenshot of the Staged Rollout pane for a configured connector.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/staged-rollout/modify-staged-rollout.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/staged-rollout/modify-staged-rollout.png#lightbox)

### Stop staged rollout

To stop a staged rollout for a connector:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Copilot** > **Connectors** > **Your Connections**.
2. Find the connector that you want to modify.
3. In the **Staged Rollout** column, next to **Staged**, choose **Edit**.
4. Choose **End Staging**, and when prompted, choose **Remove**.

[![Screenshot of the Staged Rollout pane with End Staging highlighted.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/staged-rollout/end-staged-rollout.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/staged-rollout/end-staged-rollout.png#lightbox)

Note

When you remove staged rollout, the connection results start appearing to all users in the organization who have access.

## Staged rollout limitations

The staged rollout feature has the following limitations:

- You can only add up to 100 users and 15 Microsoft 365 groups to the staged rollout list.
- The staged rollout settings are currently only applicable to Search and Copilot experiences.

## Related content

- [Deployment overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview)
