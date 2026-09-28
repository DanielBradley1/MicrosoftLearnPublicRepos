<!-- Source: https://learn.microsoft.com/en-us/entra/identity/monitoring-health/quickstart-access-log-with-graph-api -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Quickstart: Analyze a sign-in with the Microsoft Graph API

In this Quickstart, you'll use the information in the Microsoft Entra sign-in logs to figure out what happened if a sign-in of a user failed. This quickstart shows you how to access the sign-in log using the Microsoft Graph API.

## Prerequisites

To complete the scenario in this quickstart, you need:

- **Access to a Microsoft Entra tenant**: If you don't have access to a Microsoft Entra tenant, see [Create your Azure free account today](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- **A test account called Isabella Simonsen**: If you don't know how to create a test account, see [Add cloud-based users](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users).
- **Access to the Microsoft Graph API**: If you don't have access yet, see [Microsoft Graph authentication and authorization basics](https://learn.microsoft.com/en-us/graph/auth/auth-concepts).

## Perform a failed sign-in

The goal of this step is to create a record of a failed sign-in in the Microsoft Entra sign-in log.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as Isabella Simonsen using an incorrect password.
2. Wait for 5 minutes to ensure that you can find a record of the sign-in entry in the logs.

## Find the failed sign-in

This section provides the steps to locate the failed sign-in attempt using the Microsoft Graph API.

1. Sign in to [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) as a user with permissions to run a query.
2. Select **Modify permissions** to ensure you have the correct permissions.
3. Select **GET** as the HTTP method from the dropdown.
4. Set the API version to **beta**.
5. Enter the following query and select **Run query**: `https://graph.microsoft.com/beta/auditLogs/signIns?$top=10&$filter=userDisplayName eq 'Isabella Simonsen'`
6. Review the query response and locate the **status** section of the response.

![Screenshot of the query response with the error status section highlighted.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/quickstart-access-log-with-graph-api/graph-sign-in-error-sample.png)

## Clean up resources

When no longer needed, delete the test user. If you don't know how to delete a Microsoft Entra user, see [Delete users from Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users).

## Next steps

[Analyze activity logs with Microsoft Graph](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-analyze-activity-logs-with-microsoft-graph)
