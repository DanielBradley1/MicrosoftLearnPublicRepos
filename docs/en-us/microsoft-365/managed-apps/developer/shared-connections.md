<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/shared-connections?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-21 -->

# Use shared connections in an app \(preview\)

\[This article is prerelease documentation and is subject to change.\]

A shared connection lets users access a common data source through a Microsoft Copilot Managed Runtime app without creating their own connections to that source. You create the connection once and choose what the app can do with it.

For example, you might build an inventory app that lets employees look up products in a SQL database. By using a shared connection, employees sign in to the app but don't need their own SQL accounts. You can allow the app to read product information without allowing it to change or delete that information.

## When to use a shared connection

Use a shared connection when everyone using the app needs access to a common resource, such as an inventory database, and you want to manage the connection's credentials in one place.

Use a *per-user connection* instead when the data source needs to identify each person and apply their individual permissions. For example, an app that accesses a user's personal files typically needs that user's own connection.

## How shared connections work

The connection itself isn't shared directly with each app user. Instead, the app sends requests through a *connection proxy*, a service that checks each request before sending it to the connection.

Your app declares which actions it needs, such as reading a table or creating a record. The proxy allows only those actions. In the inventory example, a request to read products is allowed, but a request to delete them is blocked, even if the connection's account can delete records.

Sharing the app doesn't give users a connection they can reuse in other apps. The platform enforces these restrictions, not your app's buttons or screens. You don't need to build or configure the proxy yourself.

Important

The app accesses the data source by using the shared connection's credentials, not the individual user's. Use an account with access only to the data the app needs. Allowing an action such as reading a table doesn't, by itself, restrict which rows each person can read.

## Prerequisites

- An existing app set up for local development. See [Create an app with the Copilot Managed Runtime SDK](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-managed-apps-cli?view=o365-worldwide).
- A connection you can use, or credentials to create one, with access to the data the app needs.
- A connector and authentication type that support sharing.

To check sharing support, find your connector in the [connector reference catalog](https://learn.microsoft.com/en-us/connectors/connector-reference/). On its reference page, find **Creating a connection** and look for an authentication type marked **Shareable**. Check any product or region restrictions.

For example, the [SQL Server connector](https://learn.microsoft.com/en-us/connectors/sql/#creating-a-connection) supports sharing with **SQL Server Authentication**. Other authentication types for the same connector might not support sharing.

## Add a shared connection to your app

Add your data source, choose what the app can do, then deploy and share the app.

### 1. Add your data source

From the directory that contains your app, use the Copilot Managed Runtime CLI \(`ms`\) to add a data source with [`ms app add data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-add-data-source). For example, to add a SQL table, run:

```bash
ms app add data-source --connector shared_sql --as table
```

Follow the prompts to choose or create a connection, then select your database and table. Choose an authentication type that supports sharing. The CLI automatically configures a shared connection when the selected connection supports it.

For other connectors or for actions instead of tables, see [Connect an app to data](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/connect-to-data?view=o365-worldwide).

### 2. Set what the app can do

Your app records its permissions in `ms.config.json` as an `allowedActions` list. This list is required for a shared connection. Adding a connector makes its supported operations available in your code; it doesn't automatically allow your app users to perform all of them. If you don't set the allowed actions, users can't use the connection.

Choose either of the following options to set the allowed actions.

#### Option 1: Use a coding agent

Use a coding agent with the Copilot Managed Runtime plugin. If you didn't set up the plugin, see [Build an app with GitHub Copilot](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-github-copilot?view=o365-worldwide).

Tell your coding agent what users should be able to do. For example:

> Use the shared SQL connection for my inventory app. Let users view products, but not add, change, or delete them. Update the allowed actions in ms.config.json to match.

The plugin helps the agent find the action IDs and update the lists of allowed actions. Review the changes to make sure they match what you want users to do.

#### Option 2: Set actions manually

Open `ms.config.json` and find your shared connection under `connectionReferences`. The CLI identifies it with a populated `sharedConnectionId` field. Keep the existing connection details and add only the actions the app needs.

##### For tables

Each table under `dataSets` needs its own `allowedActions` list. Use these values:

| To allow | Add |
| --- | --- |
| Reading records | `get` |
| Creating records | `post` |
| Updating records | `patch` |
| Deleting records | `delete` |

For example, a read-only `Products` table entry looks like this:

```json
{
  "Products": {
    "tableName": "Products",
    "allowedActions": ["get"]
  }
}
```

To allow reading and updating, use `["get", "patch"]` instead.

##### For connector actions

To list a connector's actions, use [`ms connector list-actions`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-connector-list-actions) from the directory that contains your app. Replace `<connector-id>` with the connector's ID, such as `shared_sql`:

```bash
ms connector list-actions --connector <connector-id>
```

To find a particular action, add `--search`. It filters by text in the action's summary or ID. For example, to find SQL actions related to stored procedures:

```bash
ms connector list-actions --connector shared_sql --search procedure
```

Review the results and find the actions that match the operations your app calls. Copy their exact `id` values, including capitalization, rather than their display names. Choose only actions that your organization's policies allow.

Add those IDs to an `allowedActions` list directly on the connection's entry under `connectionReferences`. For example, replace `<action-id>` in the following property with an ID from the results:

```json
"allowedActions": ["<action-id>"]
```

These IDs are for connector actions. For table permissions, use the values such as `get` shown in the preceding table instead.

If your app uses both tables and actions on the same connection, include both kinds of lists: one for each table and one on the connection for the actions.

### 3. Deploy and share the app

Run the app locally with [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-dev). When it's ready, commit and push your changes, including `ms.config.json`, then [build and deploy the app](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/dev-inner-loop?view=o365-worldwide). Deployment checks that your shared connections have allowed actions configured.

Next, [share the app](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/share-app?view=o365-worldwide) with the users who need it. Share the app, not the connection. Users don't need direct access to the underlying connection.

Ask someone who doesn't own the connection to try the deployed app. Confirm that they can complete the intended tasks without creating their own connection to the shared data source.

When you add features later, update the allowed actions manually or with your agent, then deploy the changes. For example, if users now need to update product quantities, the app needs permission to update records as well as read them.

## Troubleshoot shared connections

| Problem | What to check |
| --- | --- |
| Deployment reports missing allowed actions. | Ask your agent to review the shared connections and update `allowedActions`, or add the lists manually. Every table that uses a shared connection needs a nonempty list. |
| An action doesn't work in the deployed app. | Make sure it's included in the allowed actions and that you deployed the change. The connection's account must also have permission to perform it, and your organization's policies must allow it. |
| Users are asked to create a connection. | Check that you selected a shareable authentication type. An app can also have other data sources that require each user's own connection. |
| The connection stops working for everyone. | Have the connection owner check whether its credentials have expired or its access to the data source has changed. |

## Related content

- [Connect an app to data](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/connect-to-data?view=o365-worldwide)
- [Connector reference catalog](https://learn.microsoft.com/en-us/connectors/connector-reference/)
- [Shared connections and secure implicit connections in Power Apps](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/connections-list#shared-connections-and-secure-implicit-connections)
- [Share an app](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/share-app?view=o365-worldwide)
