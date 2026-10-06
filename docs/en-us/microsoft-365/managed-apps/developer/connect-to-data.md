<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/connect-to-data?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Connect an app to data \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Microsoft Copilot Managed Runtime apps connect to data through connectors. See the [full list of available connectors](https://learn.microsoft.com/en-us/connectors/connector-reference/). You discover, add, and manage connectors from the Copilot Managed Runtime CLI \(`ms`\). You call them from your app code through strongly typed models and services that the CLI generates for you.

Read this article to learn about the connector model in apps, how to add connectors, tables, and actions from the command line, and how to debug the data layer when a request doesn't behave the way you expect.

## How connectors work in apps

A connector is a managed connection to an external system or service: SQL Server, SharePoint, Office 365, or any of the more than 1,500 available connectors. In an app, connectors give you governed access to that data without standing up your own backend or storing credentials in your code.

The following table describes the parts involved:

| Part | Description |
| --- | --- |
| **The connector** | The connector type, identified by a connector ID such as `shared_sql` or `shared_sharepointonline`. A connector exposes either *tables* \(tabular data you can query and write to\) or *actions* \(discrete operations you call\), and many connectors expose both. When you add a connector, you add one or more of its tables or actions to your app. |
| **The connection** | An authenticated instance of a connector, bound to a specific account or credential. You can reuse an existing connection or create a new one when you add a connector. |
| **The data source** | A specific table or action you add from a connector and bind to your app. Each data source has a *data source name* — a stable identifier the CLI uses to reference it in your generated code and in commands such as [`ms app refresh data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-refresh-data-source) and [`ms app remove data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-remove-data-source). |
| **Generated models and services** | When you add a connector, the CLI writes strongly typed models and services into `generated/`, recorded against your app in `ms.config.json`. Your app code imports from this folder to read and write data; you never construct raw HTTP requests against the connector. |

The Microsoft Copilot Managed Runtime SDK and host route every data call through the platform, where governance \(Microsoft Entra identity, Data Loss Prevention \(DLP\), and Advanced Connector Policies \(ACP\)\) is enforced at design time, deploy time, and runtime.

Note

Don't edit the contents of `generated/` by hand. The CLI owns these files. Use the [`ms app add data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-add-data-source), [`ms app remove data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-remove-data-source), and [`ms app refresh data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-refresh-data-source) commands to keep your local code and the platform in sync.

## Discover available connectors

Run discovery commands from the directory that contains your app so the CLI automatically inherits your environment.

List the connectors available in your environment:

```bash
ms connector list [--search <term>]
```

The output includes each connector's ID, whether it supports tabular data, and its governance status \(DLP and ACP\). Use `--search` to filter by a substring of the connector name or ID, for example, [`ms connector list`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-connector-list) `--search sql`.

To see the operations a specific connector exposes, including the DLP status of each one:

```bash
ms connector list-actions --connector <connector> [--search <term>]
```

### Why governance status appears at design time

[Data Loss Prevention \(DLP\)](https://learn.microsoft.com/en-us/power-platform/admin/prevent-data-loss) and [Advanced Connector Policies \(ACP\)](https://learn.microsoft.com/en-us/power-platform/admin/advanced-connector-policies) are admin-defined rules that govern which connectors and operations your app is allowed to use. The CLI surfaces this status during discovery so you know up front whether a connector is permitted in your environment. Seeing it at design time means you avoid building against a connector that policy blocks at deploy or run time.

Note

The business vs non-business classification feature of DLP isn't supported for apps. For more information, see [advanced connector policies](https://learn.microsoft.com/en-us/power-platform/admin/advanced-connector-policies).

## Add data to your app

Run all `add` commands from the directory that contains your app. They generate TypeScript models and services under `generated/`.

### Add a connector

Use [`ms app add data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-add-data-source) for most scenarios:

```bash
ms app add data-source --connector <connector>
```

- For a connector that **doesn't** support tabular data, the CLI adds it as an action automatically.
- For a connector that **does** support tabular data, the CLI prompts you to choose table or action in interactive mode.

In interactive mode, the CLI walks you through the full setup: choose an existing connection or create a new one, pick a dataset \(such as a SQL database or a SharePoint site\), then pick a table. When you create a new connection, the CLI first attempts a silent single sign-on. If that isn't available, or the connector supports multiple authentication types, it opens a browser-based connection flow.

### Add a table

When you already know you want tabular data, force table mode with `--as table`:

```bash
ms app add data-source --connector <connector> --as table [--dataset <name>] [--table <name>]
```

The CLI prompts for the connection, dataset, and table when you omit them in interactive mode. A connection is always required for tables, because the CLI uses it to discover the available datasets and tables.

### What happens to blocked operations

Before adding any action or table, the CLI runs a DLP/ACP check to make sure it's allowed with active policies. If a policy blocks specific operations on the connector, the CLI filters them out of code generation and reports how many it skipped, for example, *"Skipped 3 of 12 actions due to ACP policy."* If every operation is blocked, the command fails and points you to a different approach. This process keeps your generated code limited to operations your admin actually allows.

## Call data from your app code

After you add a connector, import its generated model and service from `generated/` and call it like any other typed API. The generated service handles routing the call through the Microsoft Copilot Managed Runtime host, so authentication and governance are applied without any extra work in your code.

Because the models are strongly typed, your IDE gives you autocompletion for fields and operations, and the TypeScript compiler catches schema mismatches before you run the app. Run your app locally with [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-dev) to exercise the data calls against live connections during development.

## End-user connection consent

The first time a user opens an app that uses connectors, they see a **connection consent dialog**. This dialog:

- Informs the user about the data sources the app accesses.
- Outlines the actions a connector can and can't perform. For example, an app that uses the **Office 365 Users** connector can read user profiles but can't modify or delete profile information.
- Captures the user's consent to connect to those data sources.
- Facilitates manual sign-in when needed.

Apps attempt single sign-on automatically when the user opens the app. If automatic sign-in fails, the consent dialog prompts the user to fix the connection by signing in manually. The platform can only attempt automatic sign-in when the data source preauthorizes single sign-on for the connection. For more information, see [What is single sign-on \(SSO\)?](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/what-is-single-sign-on).

## Find a data source name

Some commands, such as [`ms app refresh data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-refresh-data-source) and [`ms app remove data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-remove-data-source), take a `--name` argument that identifies a single table or action you added.

To find the data source name for a connector, open the `generated/dataSources.ts` file in your project. Each top-level key in the exported object is a data source name \(for example, `commondataserviceforapps` or `office365users`\). These keys correspond to the identifiers used by the generated service classes when making connector calls.

## Keep generated code in sync

When the underlying schema changes \(for example, a new column in a SharePoint list\), regenerate the TypeScript so your models match:

```bash
ms app refresh data-source [--name <name>]
```

Omit `--name` to refresh everything you added, or pass it \(alias `-n`\) to refresh a single table or action.

## Remove a data source

Removal commands prompt for confirmation unless you pass `--force`.

```bash
ms app remove data-source --name <name> [--force]
```

Removing a data source unbinds it from the app and deletes its generated code. It doesn't change anything in the underlying system itself.

## Analyze data requests and responses

When a data call doesn't return what you expect, debug it the same way you'd debug any web app's network layer. Apps adds no magic that hides the traffic from you.

1. **Run the app locally with [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-dev).** Local development exercises real connections, so the requests you see are the requests your app makes.
2. **Open your browser's developer tools and watch the Network tab.** Each connector call appears as a request routed through the Copilot Managed Runtime host. Inspect the request payload and the response body to see exactly what was sent and returned.
3. **Read the status code and response body together.** A `403` typically means a governance policy \(DLP or ACP\) blocked the operation; confirm the connector and operation are allowed with [`ms connector list`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-connector-list) and [`ms connector list-actions`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-connector-list-actions). A `4xx` with a connector-specific message usually points to a malformed request, such as a missing required field or a filter the connector rejects.
4. **Confirm the schema matches.** If the response shape doesn't match your generated model, the underlying schema might have changed. Run [`ms app refresh data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-refresh-data-source) to regenerate the model, then retry.
5. **Check the connection.** An authentication failure can mean the connection's credentials expired or were revoked. Re-add the connection through [`ms app add data-source`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-add-data-source) and choose to create a new connection.

Tip

Reproduce data issues locally by using [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-dev) before pushing. The local loop makes no platform build or deploy calls, so you can iterate on a failing query quickly and only push once the request behaves.
