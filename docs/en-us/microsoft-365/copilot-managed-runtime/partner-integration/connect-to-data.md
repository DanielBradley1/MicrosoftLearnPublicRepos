<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/connect-to-data?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Connect Copilot Managed Runtime partner apps to data

This article shows how to connect Copilot Managed Runtime partner apps to organizational data. When an app maker adds organizational data, the partner experience must help them discover governed connectors, bind the appropriate connection and data source, and generate typed clients for app code. The integration must surface policy decisions and actionable errors throughout that flow.

## Understand connectors, connections, and data sources

These concepts describe different parts of governed data access and are not interchangeable:

| Concept | What it is | Important scope |
| --- | --- | --- |
| Connector | Defines a service and the operations it supports. | Tenant policy can allow or block the connector. |
| Connection | Authenticates one user to a connector in one environment. | OAuth or single-sign-on connections are commonly per user. Don't copy a connection ID from one creator's workspace into another creator's project. |
| Data source | Binds selected connector behavior to an app and generates typed client code. | The binding belongs to the app. |

For the complete workflow, see [Connect an app to data](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/connect-to-data?view=o365-worldwide).

## Discover connectors

Use the following commands to discover connectors using [`ms connector list`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-connector-list).

List only connectors allowed by tenant policy:

```bash
ms connector list \
  --search "office" \
  --only-allowed \
  --json
```

To include blocked connectors and their governance status, omit the filter:

```bash
ms connector list \
  --search "office" \
  --json
```

In an explanatory partner or admin experience, show blocked connectors as unavailable and explain their status instead of offering them for selection.

Inspect connector actions:

```bash
ms connector list-actions \
  --connector shared_office365 \
  --json
```

## Recommended starting connectors

Use the following Microsoft connectors as a starting set, and check availability in the customer's environment:

- SharePoint
- OneDrive for Business
- Microsoft Teams
- Office 365 Outlook
- Office 365 Users / Groups
- Microsoft Planner / To Do
- Microsoft Forms
- OneNote \(Business\)
- Excel / Word Online \(Business\)
- Power BI

Partners should still use [`ms connector list`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-connector-list) to confirm current tenant policy because administrators might change availability.

## Add a connector

Run app-scoped data commands from the app root. For complete command syntax, see the [Copilot Managed Runtime CLI command reference](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide). command syntax.

Before using a maker's connection, configure the partner application's [required delegated permissions](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/prerequisites?view=o365-worldwide#required-delegated-permissions). Connection-use authorization for the partner application is separate from the maker's sign-in to the connector.

For an action data source:

```bash
ms app add data-source \
  --connector shared_office365 \
  --as action \
  --json
```

For a SQL table:

```bash
ms app add data-source \
  --connector shared_sql \
  --as table \
  --connection-id <connectionId> \
  --dataset <database> \
  --table <table> \
  --json
```

In interactive mode, the CLI prompts you to select or create a connection and supply missing table details. In non-interactive mode, specify `--as`. If the command can't continue without prompting, it returns an error that the partner must surface.

Tip

Some connectors require an interactive authentication flow. For connectors authenticated with Microsoft Entra, the CLI typically authenticates the signed-in user silently through their existing organizational identity and session. Other connectors might require the partner experience to guide the user through connector-specific authentication and collect required setup inputs. Don't collect or store raw user passwords or secrets. Start with Microsoft Entra-authenticated connectors because they provide the simplest authentication experience.

## Persist and use generated code

Adding a connector generates schemas and typed client code in the app that the app can use to communicate with the connector.

After adding a connector:

1. Persist the changed `ms.config.json`, generated TypeScript under `generated/`, and local schemas under `.ms/schemas/`.
2. Import the generated service in app code.
3. Run the app build.
4. Test the operation inside Local Play as the signed-in user.

After an underlying schema change, regenerate clients for all bound data sources or optionally one named data source:

```bash
ms app refresh data-source [--name <name>]
```

## Remove a data source

The same removal command applies to table and action data sources. See the [connector guide](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/connect-to-data?view=o365-worldwide#remove-a-data-source) and [CLI reference](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-remove-data-source).

Removal prompts for confirmation unless `--force` is passed:

```bash
ms app remove data-source \
  --name <name> \
  --force \
  --json
```

Removing a data source unbinds it from the app and deletes its generated code. It does not alter the underlying external system.
